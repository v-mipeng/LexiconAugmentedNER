# LexiconAugmentedNER
This is the implementation of our arxiv paper "[Simplify the Usage of Lexicon in Chinese NER](https://arxiv.org/pdf/1908.05969.pdf)", which rejects complicated operations for incorporating word lexicon in Chinese NER. We show that incorporating lexicon in Chinese NER can be quite simple and, at the same time, effective.

# Source code description
## Requirement:
Python 3.6
Pytorch 0.4.1

## Input format:
CoNLL format, with each character and its label split by a whitespace in a line. The "BMES" tag scheme is prefered.

别 O 

错 O

过 O

邻 O

近 O

大 B-LOC

鹏 M-LOC

湾 E-LOC

的 O

湿 O

地 O

## Pretrain embedding:
The pretrained embeddings(word embedding, char embedding and bichar embedding) are the same with [Lattice LSTM](https://www.aclweb.org/anthology/P18-1144)

## Run the code:
1. Download the character embeddings and word embeddings from [Lattice LSTM](https://github.com/jiesutd/LatticeLSTM) and put them in the `data` folder.
2. Download the four datasets in `data/MSRANER`, `data/OntoNotesNER`, `data/ResumeNER` and `data/WeiboNER`, respectively.
3. To train on the four datasets:

- To train on OntoNotes:

`python main.py --train data/OntoNotesNER/train.char.bmes --dev data/OntoNotesNER/dev.char.bmes --test data/OntoNotesNER/test.char.bmes --modelname OntoNotes --savedset data/OntoNotes.dset `

- To train on Resume:

`python main.py --train data/ResumeNER/train.char.bmes --dev data/ResumeNER/dev.char.bmes --test data/ResumeNER/test.char.bmes --modelname Resume --savedset data/Resume.dset --hidden_dim 200`

- To train on Weibo:

`python main.py --train data/WeiboNER/train.all.bmes --dev data/WeiboNER/dev.all.bmes --test data/WeiboNER/test.all.bmes --modelname Weibo --savedset data/Weibo.dset --lr=0.005 --hidden_dim 200`

- To train on MSRA:

`python main.py --train data/MSRANER/train.char.bmes --dev data/MSRANER/dev.char.bmes --test data/MSRANER/test.char.bmes --modelname MSRA --savedset data/MSRA.dset`

4. To train/test your own data: modify the command with your file path and run.

