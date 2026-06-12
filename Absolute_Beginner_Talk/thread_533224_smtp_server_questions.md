---
title: "smtp server questions"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by drewsmug on 2007-08-23
thanks for reading this.
i just recently setup a lamp server on Feisty. i was happy with myself.  i have apache2 php5 and mysql running.  my purpose in this was to setup my phpbb2 forum.  which is running alright.

i want to be able to setup a smtp server now so that i can send mail out to all the members.  also so i dont get a mail error message when people sign up.  and just because i want to learn how to do it.

my first questions are what are some good opensource (or in other words free) smtp servers that will be good for somebody doing this for the first time.

and also i looked for some tutorials but didnt come across anything yet.  are there any good ones that could help me get hands dirty.  thanks for any and all help.

---

### Post by southernman on 2007-08-23
One word... Postfix

A really good walk through is [right here]("http://doc.ubuntu.com/ubuntu/serverguide/C/postfix.html").

---

### Post by drewsmug on 2007-08-24
i got stuck.
at the 'SMTP Authentication' section it says just use the postconf command to edit some files.  i dont actually understand that.  i tried just entering those next lines into my terminal but that was no good.

i tried just looking for the files but '/etc/postfix/sasl/smtpd.conf' doesnt even exist and i dont think that is what it is asking since the instruction are unclear (atleast to me)

a push in the right direction please

---

### Post by southernman on 2007-08-24
Not sure if you wanna listen to anything I have to say after that. Turns out that tutorial is not written out so well. They ask you to configure something that was not directed to install until later on in the tutorial. Sorry about that... I won't be linking to that piece of flubbed up mess again.

Instead, [this one]("https://help.ubuntu.com/community/Postfix") looks to be a bit more complete and in order. 

Please, before you go another step further with this, have a look [at the postfix website - documentation]("http://www.postfix.org/docs.html"). I am taking my own advice as I type this... well ok, so I took a break to reply to this and break some of the cob webs loose. ;)


Again, my apologies. You could do sudo aptitude purge postfix, which will remove the program and purge the config files too.

They say experience is the best teacher, so brother... were one step closer to graduation day! ;p

---

### Post by wolfear on 2007-08-26
As I am in process of setting up a mail server and pounding my head on the desk, thought I'd drop a line.

The tutorial I have been primarily using is [http://flurdy.com/docs/postfix/]("http://flurdy.com/docs/postfix/")

Most of the head pounding is my fault, not the tutorials..lol.

---

