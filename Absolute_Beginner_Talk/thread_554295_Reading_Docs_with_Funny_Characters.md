---
title: "Reading Docs with Funny Characters"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Deborah Norling on 2007-09-18
When I install new apps, I know I can find docs in /usr/share/doc/PACKAGE_NAME.  But often, I encounter text files with funny characters that make them hard to read. For example, I recently installed the simple mailx so I could send mail on the command line.  I know I can type man mail or info mail, but I also wanted to read the manual.txt that appeared to be newer, more complete documentation located in /usr/share/doc/mailx. Here are a few sample lines:

     ESC[1m1.  IntroductionESC[0m                                               
          ESC[4mMailESC[24m  provides  a simple and friendly environment for sen
ding and                                                                        
     receiving mail.  It divides incoming mail into  its  constituent  mes-     
     sages  and  allows  the user to deal with them in any order.  In addi-     
     tion, it provides a set of ESC[4medESC[24m-like commands for manipulating  
messages                                                                        
     and sending mail.  ESC[4mMailESC[24m offers the user simple editing capabil
ities to                                                                        
     ease the composition of outgoing messages, as well  as  providing  

... you get the idea. How can I read these "manuals"?

---

### Post by matthew.lns1 on 2007-09-18
I would try using Yelp, the Ubuntu help browser.

---

### Post by Deborah Norling on 2007-09-29
Yelp is a great idea for most users, but for me there are two problems. First, this is a server box. X isn't installed -- I just ssh in from a PC. Second, I'm visually impaired, and even if I were to install X I don't think Yelp works too well with Orca. There's got to be an old-style geeky unix way to read this stuff!!!

---

