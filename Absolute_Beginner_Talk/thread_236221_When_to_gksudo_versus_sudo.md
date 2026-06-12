---
title: "When to gksudo versus sudo??"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-14
Hi Everybody,

Well. It's been a little over a week since I completely switched to Ubuntu on my ThinkPad and with the help and patience of many of you, I have gotten things pretty well sorted. My wifi works, I can watch DVD's and stream almost anything, all my audio works, and I am not having too much trouble adding/removing software with apt-get, aptitude, or Synaptic. So far, so good.

Here's my question:

I am still up in the air about when to use gksudo instead of sudo (or vice versa). I have read the manual and the wiki, and I understand that I'm not supposed to use sudo with graphical apps., but what about things like gedit?  See, I just don't gedit!!:shock:  Alright, I realize that was uncalled for, but can anyone straighten me out about when exactly it's appropriate to use sudo, and when by doing so I run the risk of screwing something up?

TIA for your patience and assistance.

Kent

---

### Post by davebgimp on 2006-08-14
> **Carbonfish said:**
> Hi Everybody,

Well. It's been a little over a week since I completely switched to Ubuntu on my ThinkPad and with the help and patience of many of you, I have gotten things pretty well sorted. My wifi works, I can watch DVD's and stream almost anything, all my audio works, and I am not having too much trouble adding/removing software with apt-get, aptitude, or Synaptic. So far, so good.

Here's my question:

I am still up in the air about when to use gksudo instead of sudo (or vice versa). I have read the manual and the wiki, and I understand that I'm not supposed to use sudo with graphical apps., but what about things like gedit?  See, I just don't gedit!!:shock:  Alright, I realize that was uncalled for, but can anyone straighten me out about when exactly it's appropriate to use sudo, and when by doing so I run the risk of screwing something up?

TIA for your patience and assistance.

Kent

Good question. Personally, I rarely ever use gksudu (or in my case with Kubuntu 'kdesu') and it doesn't seem to cause me issues. I just 'sudo program &' and I'm usually cool.

---

### Post by Kobalt on 2006-08-14
I use "sudo" when using the command line, and gksudo when I want to launch an app with root permission. The main difference I get from my little experience is that the app remain open even though you close a console with gksudo. 

Cheers !

---

### Post by steve.horsley on 2006-08-14
My understanding is that you should use gksudo any time you launch a GUI application, and that includes nautilus, gedit etc. It probably even includes gnome-terminal. The problem that using sudo occasionally causes is that a hidden file .ICEauthority somehow gets created in your folder and left with root ownership, and this prevents launching other non-root apps until you delete that file.

---

### Post by Carbonfish on 2006-08-14
Thanks for the feedback guys, 

I really want to understand this since I'm still pretty n00bly and don't want to have to put out any more fires than necessary.

I'll keep watching this thread and glean all the insights that I can from you all.

Thanks again,

KC

---

### Post by PriceChild on 2006-08-14
[http://psychocats.net/ubuntu/graphicalsudo.php](http://psychocats.net/ubuntu/graphicalsudo.php)

Explains it very well :)

---

### Post by Carbonfish on 2006-08-14
Thanks everybody, and thanks Price Child for the link.

---

