---
title: "Cannot get MOL going??"
date: 2006-10-13
forum: Apple PPC Users
---

### Post by ricanelite on 2006-10-13
Alright, I have MOL "Maconlinux" installed got all the drivers going

Now when I try to run it "startmol" I get this message
[B]
"No video modes have been configured. Please run 'molvconfig'
 as root to configure full screen video or disable console
 video in /etc/mol/molrc.video."[/B]

Now when I type in **sudo molvconfig**the monitor goes black and nothing happens so I have to do CTRL+ALT+F7 for me to get out and return back to my Linux Desktop.

Now, I dont know what the heck to do! I looked at several sites and cannot find anything that will explain it to me in a easy way. I'm a newbie to this and I'm willing to learn. So if you someone could explain to me how I could get this going. That will be great!!! Thank you so much!:)

---

### Post by munchbach on 2006-10-14
try "startmol -X" and see if it starts window in window.

Cheers.

---

### Post by ricanelite on 2006-10-15
Well I got the same message

I dont know what is going on?

But so far I have headed over to the Ubuntu Channel and MOL Channel in IRC Chat. So far I have not found anybody that could bare with me and help me out. It is so hard when your new to the Linux Environment and trying to get things working so that you wont miss the Operating System you have used in the pass. As for myself it was OSX. Since I have seen Linux and the screenshots I always wanted to use it and Explorer the Environment. But now I willing to learn as much as I can and even though it has been 4 days I have been using Ubuntu Linux I have ripped music cds to linux and also have been downloading my Podcasts which was my main concern.

---

### Post by techrush on 2006-10-15
MOL can be a bit of a black art at times to get it doing what you want.

it sounds like the molvconfig script isnt finding any suitable video modes. what kind of mac are you on and what is the resolution/refresh rate of your monitor ?

---

### Post by ricanelite on 2006-10-16
okay it is a Mac mini running a G4 

My monitor is could go with a max of 1280 x 1024 and a refresh rate of 60.

Does that sound right?

Please let me know. Thank you for responding.

---

### Post by munchbach on 2006-10-16
> **ricanelite said:**
> okay it is a Mac mini running a G4 

My monitor is could go with a max of 1280 x 1024 and a refresh rate of 60.

Does that sound right?

Please let me know. Thank you for responding.

I would try 1024x768 first just to be safe. When you run:

```
sudo molvconfig
```

Cheers.

Andrew

---

### Post by ricanelite on 2006-10-16
Well when I do "sudo molvconfig" My Monitor goes black and I have to hit CTRL+ALT+F7 to return back to my terminal and Linux Desktop.

On the irc chats in the #MOL Channel and Ubuntu they told me I have to edit one of the files. But the problem is 

1. I dont know how

2. I need guidance because since I'm new to Linux it takes me longer to understand certain things. So on each step I always have questions. Which made people in the irc chat a little annoyed. So it has been hard for me to get things going.:(

---

