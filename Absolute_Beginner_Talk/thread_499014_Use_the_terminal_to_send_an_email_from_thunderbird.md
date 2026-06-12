---
title: "Use the terminal to send an email from thunderbird"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by Enalia on 2007-07-12
I'd like to be able to send email through the terminal, or in a script, if possible.  I'd really REALLY like to be able to do it with thunderbird but If i have to get another program I suppose I will.

However if anyone knows of  a way to do it with thunderbid, it'd be much appreciated.

Thanks in advance.

---

### Post by Blutack on 2007-07-12
I'm afraid thunderbird is a mainly GUI orientated program and therefore can't do what you want.

However MUTT
[http://www.mutt.org/](http://www.mutt.org/)
Has an extensive list of command line options including sending an email from the command line.
[http://www.mutt.org/doc/manual/manual-6.html](http://www.mutt.org/doc/manual/manual-6.html)

Install it with
> sudo aptitude install mutt
from a terminal or use Synaptic Package Manager (In Settings --> Administration).

Hope this helps!

---

### Post by Enalia on 2007-07-12
I'm sure that'll work fine....

but, if possible, i'm looking for something that, once set up, could send mail with something like

mailprog -t "Whoyouare@sendingmail.to" -s "Subject" -c "content and such"

the bit about content being part of the same line is sort of important for me.

Actually though I'd settle for something easier than mutt, if there is anything.  Anywho I suppose i'll sit here and try to learn me some mutt.  I imagine once i can get this to work with gmail it'll be smooth sailing

---

### Post by UnixAnt on 2007-07-12
Sendmail is probably what you are looking for.

You can do precisely what you are trying to achieve, and it can be called from a shell script, etc to suit your needs.

Sendmail is highly configurable, but tends to have a relatively steep learning curve too.  Perhaps exploring this avenue is what you are looking for?

The Sendmail man page is excellent, and would be my first choice before delving into online resources ;)

---

### Post by cwmoser on 2007-07-12
Use the command line "mail" command like this example:

me@klaatu:~$ mail  [email]help@yahoo.com[/email]
Subject: Test of the mail command
Dear Sir,
This is a test of the mail command
run from the command line without
a GUI interface.  Sure its "old-school"
but sometimes the old way can be
the better way.
.
Cc: 
me@klaatu:~$ 


Note that [email]help@yahoo.com[/email] is the mail recipent, and when you enter the body of the mail message you need to insert carriage returns.  Also, to end the mail body text, enter a period on a blank line.

I remember this from the old days when I was a Unix C-programmer.

Carl

PS:  If the mail command does not exist, go to Synaptic and install mailx

---

### Post by Waappu on 2007-07-12
> **Enalia said:**
> I'd like to be able to send email through the terminal, or in a script, if possible.  I'd really REALLY like to be able to do it with thunderbird but If i have to get another program I suppose I will.

However if anyone knows of  a way to do it with thunderbid, it'd be much appreciated.

Thanks in advance.

Hi

See if this helps you
[http://www.mozilla.org/docs/command-line-args.html#Syntax_Rules](http://www.mozilla.org/docs/command-line-args.html#Syntax_Rules)

---

