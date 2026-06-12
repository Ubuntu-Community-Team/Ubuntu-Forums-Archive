---
title: "I wanna run socket program in ubuntu"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by pmn.blazer on 2008-03-26
Hello ..
i want to run socket program in _ubuntu_ that **server.c** and **client.c** to connect with TCP protocol, So how can I do it??which package or which adding to run this sockets program..


pls help me...It is very important for my assignment...most my friends said to get out of group. :(

---

### Post by pedro_orange on 2008-03-26
Well if they're .c files you'll have to compile it first.

Look in the Forums Programming Talk sections for advice on that front. But (if it's c++) you'll probably just need to do: g++ -Wall -pedantic server.c -o server.o

And then run it with ./server.o

So do that, and I presume you'll have to run the client and server on different machines to achieve the client/server topology.

I can't really give anymore advise without actually looking at the code and see how it expects to be setup. You should consult the documentation you have regarding these files.

If this is for a school assignment, your tutors should help you to set it up. They are there to help you after all. It's their job.

---

