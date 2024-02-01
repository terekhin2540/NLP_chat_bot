# NLP_chat_bot

This project is divided into three main parts, namely, analysis (Investigate dataset), training (Train and evaluate models) and bot (Add voice interactivity and Potential extensions). We have chosen to investigate and build our final bot on SQuAD2.0 dataset. Our final goal was to build a question answering game, utilizing a transformer bot and speach-to-text and text-to-speach modules.

This project consists of several steps:
1) fine-tuning a pre-trained transformer (bert-case-uncased) on the squad dataset. Like most traditional models and in line with our dataset, model takes as input the concatenation of a question and a context that contains the answer to that question. It then outputs the indices that are then used to extract the predicted answer in that context.
2) from huggingface, testing a more advanced bert pre-trained model that was already fine-tuned on this exact task and dataset. For uniformity, when evaluating these models, we kept the testing process the same while changing the tokenizers etc. as necessary.
3) testing a well-known LLM (gpt-2) on this task but without access to a context, without any prior training, and on mostly unseen data. Our goal was to evaluate the adaptability (or lack thereof) of gpt-2 on such a difficult task (question given, no context given, no fine-tuning) where it had to reference its pre-training data to predict an answer.
4) building question-answering game bot. Turn by turn, the player and the bot each ask each other a question that should be answered. If the player or the bot answers a question correctly they/it gain/s a point. The first to reach 2 points wins the game. On the player's turn, the player asks the bot a question using their voice. The bot transcripts that voice file and using the dataset, word2vec and cosine similarity, matches the user's question to a title and presents the user with 5 titles which they confirm is related to the question. Afterward from the dataset, the bot searches for the items containing that title and runs the similarity search on all of the contexts to find the related context for the question. The bot then, using the question and the predicted context, predicts an answer to the question. Also speaking it out as a voice file. Lastly, the user confirms if the question is correct or not. In Bot's turn, the bot randomly samples 5 titles and presents them to the player. The player chooses which title they want to be questioned on. Using that title, the bot, samples a related question and asks it to the user. By recording their voice, the user answers the question. Similarly, after transcribing the recording, the bot (using word2vec, cosine similarity, and a threshold) gives his evaluation of the correctness of the answer
