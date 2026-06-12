---
title: "Installing Open Office"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by fenwick on 2006-09-30
So I got my Xubuntu disc and Open Office disc in the mail.  Xubuntu working great and I love it, although I am very very new to this whole Linux thing.  Not a clue actually.  

Problem is I can't get the Open Office to install.  No idea what to do.  Can open it and look in wonder at all the folders, thats it.

Out of interest, why doesn't it self-install?  Am I being simplistic?

More importantly how can I get it to install.  Help please.  I really need to get the presentation thing (PowerPoint alternative) working. 

Thanks

---

### Post by wpshooter on 2006-09-30
My I ask why you are installing Xubuntu instead of just Ubuntu (plain) with gnome interface ?  Is it a matter of available memory, etc. ?

With that you get Open Office preinstalled.

---

### Post by Kateikyoushi on 2006-09-30
Is that the linux version of openoffice ? Sorry if it sounds like a stupid question yesterday someone tried to install photoshop in linux.
Honestly I've never even seen an openoffice cd, but I would recommend installing it from the repositories.
To do that type

```
sudo aptitude update
sudo aptitude install openoffice.org
```

---

### Post by fenwick on 2006-09-30
I didn't realise that Ubuntu came with OO preinstalled.  I liked the idea of a really simple and light (fast) GUI so I went for Xubuntu.  Mistake.  Bit of an older laptop and I am a  bit impatient though.

---

### Post by Kateikyoushi on 2006-09-30
I have a quite small 2 years old notebook with a 1Ghz pentium M and 512 Mb ram and ubuntu gnome flies on it compared to windows.

---

### Post by petri on 2006-09-30
Xubuntu is better if you have less than 256mb RAM.

Can you find Synaptic or Adept in Xubuntu? With those two you can install everything you might need. Well, almost. Anyway OO is there ;)

Otherwise just paste the lines Kateikyoushi wrote in terminal, press Enter after each line.

---

### Post by fenwick on 2006-09-30
> **Kateikyoushi said:**
> Is that the linux version of openoffice ? Sorry if it sounds like a stupid question yesterday someone tried to install photoshop in linux.
Honestly I've never even seen an openoffice cd, but I would recommend installing it from the repositories.
To do that type

```
sudo aptitude update
sudo aptitude install openoffice.org
```

Yup, Linux version.   Problem is I can't connect that laptop to the internet yet, Linux not recognising my inbuilt wireless card etc.  I ordered the CD from one of those people who sell them for next to nothing, thinking that would make it so much easier and more simple.  Now I am stuck.

---

### Post by wpshooter on 2006-09-30
What kind of internet connection do you have ?  Do you have DSL ?  Do you have another computer which is connected that you can use to download Ubuntu/gnome 6.06.1 - DESKTOP or perhaps ALTERNATE version.  That would be my recommendation.  If your computer has enough memory, I think you should give Ubuntu/gnome a try.

---

### Post by fenwick on 2006-09-30
I have a wireless connection because I am too rural to get copperline broadband.  I do have another computer running on Windows that is connected.  Can I download Ubuntu and burn to disc and then install.  Or should I load Windows on my laptop, connect to the internet and then install direct?  Sorry for the stupid questions. If I sound like a beginner then you guessed right.  

By the way what is the alternate version?  How does it differ from the Desktop.

---

### Post by petri on 2006-09-30
Start the program I mentioned above, put your CD in drive and configure your Synaptic so it can see your OO_CD. Then paste the commands inte terminal above.


EDIT How much RAM you have?

---

### Post by fenwick on 2006-09-30
Sorry for the delay.  I have 256 RAM.

---

### Post by fenwick on 2006-09-30
Hi Petri
I am at work at the moment but I do remember seeing Synaptics on my system.  Will try that out tomorrow and let you know.  The commands I paste, would that be the ones that Kateikyoushi gave?

Thanks for your help, really appreciate it.

---

### Post by petri on 2006-09-30
Yes. You also have to hear the cdplayer to spin up when you update. I have never used cd som I'm not so sure about it but it won't brake your machine anyway :rolleyes:

EDIT: Here's about Synaptic and adding an CD. It's for Breezy but you'll get the idea. [https://help.ubuntu.com/community/Repositories/Ubuntu#head-7b4ba9c71df331383c85fa08d14bca91a24ce17a](https://help.ubuntu.com/community/Repositories/Ubuntu#head-7b4ba9c71df331383c85fa08d14bca91a24ce17a)

---

