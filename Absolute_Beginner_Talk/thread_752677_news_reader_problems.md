---
title: "news reader problems"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by methodtwo on 2008-04-11
hi there, I made a .newsrc file for the gnus news reader...it looked like this
(setq gnus-select-mothod '(nntp "myisp.com"))
I then did M-X-gnus in emacs and got nntp (news) open error: ' '. continue ? (y or n)
Does anyone know how i could get gnus working here?

I also tried tin...did $export NNTPSERVER=myisp.com and new.myisp.com in /etc/nntpserver and then tried $tin -r and $tin -r myisp.com ....but i got a permission denied error.....so i did $sudo tin -r   
and $sudo tin -r myisp.com,  but still got a permission denied error
Does anyone know what i could do to get tin working on ubuntu?

Lastly i tried pan.I followed to wizard the first time i started pan up ie i filled in the nntp server box etc.So when it started it asked me if i wanted to download a list of news groups from the server.Well i left it to do this task for a long time but nothing happened!.I guess it could not connect to the server.Any clues?

If there are any pages with a walk-you-through tutorial for any good news reader(that works!)for ubuntu then that would be greatfully recieved too
Thankx in advance

---

### Post by Martje_001 on 2008-04-13
If you do:
```
telnet your.isp.com 119
```
in a terminal, do you get any connection?

---

### Post by Zill on 2008-04-13
First, make sure you have all the info required from your ISP such as the newsserver (news.myisp.com) and the port number (usually 119).  Some ISPs will also require newsserver authorisation consisting of a username (name@news.myisp.com) and a password.

Pan is the default Gnome newsreader and should work fine when setup correctly with this info,   However, I prefer to use Claws Mail (in the repos) for newsgroups.

---

### Post by the mighty windle on 2008-06-01
I'm having a different issue with Pan. Every time I launch it and then try to view and refresh the unsubscribed groups it just bugs out and shuts down on me. Any ideas please? I am using Hardy Heron and the latest version of Pan.

---

### Post by Martje_001 on 2008-06-01
If you type pan in a terminal to start it, and then do the same, what does it say?

---

### Post by Zill on 2008-06-01
the mighty windle:  More info required I think...

1)  Has Pan ever worked correctly for you in Hardy?  If so, this confirms that your configuration is correct.  If not then double-check your settings.

2)  What is the exact error message you get when it "bugs out"?

---

### Post by the mighty windle on 2008-06-01
The latest version of Pan has only worked once in Hardy before it just disappeared. Unfortunately it doesn't display any error message, it just closes down :confused:

---

### Post by the mighty windle on 2008-06-01
I've just tried launching it from the console and got the error message "Segmentation fault"

---

### Post by Zill on 2008-06-01
If you are using Pan 0.129 then this *may* be related to bug [72962]("https://bugs.launchpad.net/ubuntu/+source/pan/+bug/72962").

If this is the case then you could add your confirmation to Launchpad and wait for resolution :(

Alternatively, you could try Claws or Thunderbird to see if they are suitable.

---

### Post by the mighty windle on 2008-06-01
Yeah seems like the same problem. Thanks for the advice anyhoo :) I'll try something else in the interim.

---

