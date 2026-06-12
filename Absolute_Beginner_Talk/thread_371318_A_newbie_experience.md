---
title: "A newbie experience"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by lighthousewilly on 2007-02-26
Just thought I would share my trials and tribulations as a total newbie to Ubuntu/Linux. 

I am totally new to Ubuntu and linux, I have been trying to make the switch for sometime now and I finally had a free laptop to load it on and just experiment with. Here is what I have.

Dell Inspiron 2500 1ghz 512MB RAM 40GB
Linksys PCMCIA WPC54G Wireless Card
Ubuntu 6.06 LTS
[Ubuntu Linux Bible]("http://www.amazon.com/Ubuntu-Linux-Bible-William-Hagen/dp/0470038993/sr=8-5/qid=1172536797/ref=pd_bbs_sr_5/105-4131706-7014049?ie=UTF8&s=books")

Downloaded from the site like everyone else, created my ISO then pretty much installed with no problem onto my laptop. The real fun came when I went to install the wireless drivers for my card. Some things I learned.

1. If you’re going to use a program in terminal the term “sudo” before, gives you the permissions to make changes soooo…. 

sudo ndiswrapper –l  

Will list the driver that is currently in use. If you try ndiswrapper -i it wont do anything as you wont have permissions. 

2. You can figure out what folder you’re in when you first get into terminal by typing in 

pwd 

3. To change directory, first type dir and see what’s available, then type 

cd <dir>

4. If you’re going to use ndiswrapper to map to your drivers, need to make sure if you have a Linksys router and you have the updated .inf and .sys file in the same folder. The easiest thing for me was to navigate to the folder that contained the file, then all I had to do was type in ndiswrapper –I  lsbcmn.inf 

5. For me, things were easier when I just did “sudo bash” which gives you the permissions you need to get what you’re doing done quickly

6. Restart, restart, restart

7. Get a book and look through these forums 

8. wifi radar didn’t work for me with my home network, could be an error on my part, but I don’t think it supports wep encryption, going into network connections and working from there did the trick for me. wifi radar is good though for a graphical representation of available local networks. 

9. I broke my Synaptic Software library by inserting the disc that came with my book, its a copy of 6.10 and for whatever reason, it broke the library. Don’t know why and don’t know enough about it to speculate. I wouldn’t do it if you are an extreme novice like me. 

10. I have probably made errors in this, just let me know if I have

11. Now I am connected to the internet, what next? I am going to try and streamline my installation and make it faster. There is a lot loaded that I don’t know if I need, these forums help quite a bit, cant stress that enough. 

12. Just tried to share what I remember from the past few days, learned a lot and I really like Linux also still new to the forums, thought this was the best place to post this...hope this helps someone else.

---

### Post by wesley_of_course on 2007-02-26
Wesley here ;
                            Bravo , well put .

  Welcome and hang on this is a Blast !

    Fellow Newbie myself .

---

