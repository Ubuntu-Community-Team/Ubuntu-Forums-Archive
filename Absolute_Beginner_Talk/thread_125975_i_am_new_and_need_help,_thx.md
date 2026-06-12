---
title: "i am new and need help, thx"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by Nabba on 2006-02-05
Hello, I am very new to Linux in general, ok so I have download and burned the “live CD” of ubuntu, it works well on my laptop but I have a few issues and lots of questions so bear with me:


First the “issues” I don’t know if it is because it is running off the “live CD” and installing it fully would solve it. BTW I have an Acer Aspire 1642WLMi (v2) 

1.	The sound does not work…I don’t really have too much exp with Linux normally I would try to reinstall driver or something? So anyway I took screen shots to help u to help me. Here is the screen shots of my device manager (the top part) [http://nabba64.co.uk/new_page_4.htm]("http://nabba64.co.uk/new_page_4.htm")
And the middle and bottom [http://nabba64.co.uk/new_page_5.htm](http://nabba64.co.uk/new_page_5.htm) 
Also sound preferences [http://nabba64.co.uk/new_page_6.htm](http://nabba64.co.uk/new_page_6.htm), I can put up a screen shot of any thing u need to see 


2. 	ok, next “issues” is that I can get my wireless internet to working but it does not work when I have wep enabled in my router, I have try to put in my hex code in this windows [http://nabba64.co.uk/new_page_2.htm](http://nabba64.co.uk/new_page_2.htm) I have tried both formats 12-23-34-45-56 and just in 1223344556 (btw they are not my real codes I just made them up to explain)

3. my screen runs at 1280 x 800 in xp but in ubuntu it runs at 1024 x 786. it looks ok in ubuntu but not when I go on the internet all the written looks fuzzy and I can not make it driver it higher. I tried to run it higher here [http://nabba64.co.uk/new_page_3.htm](http://nabba64.co.uk/new_page_3.htm) but did not have any higher res

Right and now to the questions
4. I need to use lots of PDF files (for manuals for boilers) can I open them under Linux in anyway
5. I need to use msn, I understand there is an IM in ubuntu but does not work with msn so is there program I can use to get it to work like wine?
6. Right please look here [http://nabba64.co.uk/new_page_1.htm](http://nabba64.co.uk/new_page_1.htm) can I install ubuntu in dev/hda5 or do I need to partition it anyway? (Btw xp is installed in dev/hda2 I think)
7. and last one I like too use swishmax for making flash stuff (nothing to hardcore I just liking messing about with it) is there a Linux replacement and is easy to use or is it a wine job again

I have numbered them so I can keep track of what u are answering 

If u want me to get anymore screen shot I can, and if I just being a dumb *** u can tell me as well and I must say I am looking forward to moving to ubuntu.

---

### Post by bartbes on 2006-02-05
1. don't know
2. Search the forums
3. Start Live CD in advanced mode, and at install it is asked
4. yes
5. Gaim is included, so it is already done.
6. You need to partition, just do it at the setup. (you also need to assign a swap then)
7. don't know

---

### Post by Nabba on 2006-02-05
ok i found the answers to 7, 5, 4 in [http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html) :-D 
ok i will look in to the forum in a bit more detail, sorry
and what is a swap is that a the bit that asks u at the start what os u want:confused: 

i will look in to the forum more

---

### Post by saubz on 2006-02-05
4.) to get acrobat reader and plug-in for firefox

```

sudo apt-get install acroread
sudo apt-get install mozilla-acroread
sudo apt-get install acroread-plugins
killall gnome-panel

```

---

### Post by bartbes on 2006-02-05
a swap partition/swap memory is the virtual memory of linux, usually twice as big as your normal memory (and that's in most cases more then enough)

and to 4 (again) you actually don't need acrobat/adobe reader because there is standard an pdf viewer in ubuntu

and the bit that asks what u want to boot is called the MBR (Master Boot Record) in Ubuntu Linux it's standard GRUB (don't know where it stands for)

---

### Post by Mustard on 2006-02-05
For fixing your screen resolution, I would have a read over this thread, which covers the issue pretty comprehensively...

[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

For your WEP problem, I would have a read on this wiki page...It has a little section on WEP that might give you some clues as to how you might get things working...

[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

