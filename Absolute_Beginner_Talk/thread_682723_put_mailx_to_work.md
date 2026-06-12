---
title: "put mailx to work"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by JoaoCarlosCorreia on 2008-01-30
Hi, I'm using ubuntu 7.04 

I'm trying to send an e-mail via command line.
For that I guess I can install mailx, right?
I did apt-get install mailx.

And now?
What should I configure a more in my Ubuntu to do what I want?

If someone could explain with every single step (even that one you think is obvious) would be great, because i read a lot of tutorials and still got nothing.

I tried the command: 
```
mailx -s "This is my subject" jcor@sapo.pt
This is the body of my email
CTRL-D
ENTER

```
But I didn't receive nothing in [email]jcor@sapo.pt[/email]

Can someone give me some help on this?

Thanks a lot,

João Correia

---

### Post by steak on 2008-02-13
Hey João,

Yep mailx is the package for you.

The next thing to do is to see where your email has got to.

Look in /var/mail/<user> . If the sapo.pt SMTP server has bounced your message back for some reason that will say.

```

less /var/mail/<user>

```


The other place to look is in the mail queue, to see if the email has left your computer. mailq should be saying "Mail queue is empty".

```

$ mailq
Mail queue is empty

```

---

