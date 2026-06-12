---
title: "Using Vi editor as an email editor"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by utab on 2006-04-15
Dear all,

I am using VI for my text work all the time (Most of the time for programming stuff). Pretty fine editor.

I would like to use it to write and read emails as well and most importantly I want to use the command line for email operations.

Detailed explanations for these purposes are higly welcomed...

Thx in advance.

---

### Post by bscbrit on 2006-04-15
I think that there are 3 parts to the answer to your question.  The first is which Mail Transfer Agent to use.  There are quite a few but Postfix and Sendmail are the most common with the former being easier to configure.  But there are others and I'm sure there will be plenty of suggestions for their own 'favourite'.

I use fetchmail to collect my mail from ISPs and external mail servers.  And you can use 'mail' to send mail from the command line.  But again, there are lots of possibilities - pine and mutt are just 2 that spring to mind.  Try your own computer as a source of information:

man fetchmail
man postfix
man sendmail
man mail
man pine
man mutt

These are all rather dry and difficult to digest, but do contain all the information you need if you can only understand it - I find it better to Google for the commands and get different explanations.  Eventually, I begin to get the idea - but perhaps I'm just not very bright...:-?

---

