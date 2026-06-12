---
title: "belkin, wireless g card can't connect to internet"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by nicolino101 on 2007-03-10
This is quite the conundrum. 
I've installed ubuntu dapper drake on my ibm thinkpad. It works but I can't connect to the internet using my... 
belkin wireless g card
Model # F5D7010 
compatible with 802.11b and 802.11g - whatever that means?

Someone  was trying to help me last night and gave up. I can't say I blame him. He said something about an e100 module in the kernel...  but this is all Greek to me.

I am a complete beginner when it comes to linux, but I'm actually a professional web programmer. I've run many apps on linux, just never had to set it up till now.

The card works great on win xp and win 2000 pro.

I need to get a lamp stack working and I think I could do that with internet.

Also I can't seem to get ./configure make install working. Ubuntu complains there is no such file or directory and I can't seem to find it either.

/bin holds executables... cat, gunzip, tar, etc.... correct?
./configure ...ubuntu says no such file or directory - where is it?
make... does not work.. where is it? - how do I make it work... are these executables?
I do a find... from find / make ...  and ubuntu says ... no such file or directory?

Please help before I lose the rest of my hair!!!

              Nicolino

---

### Post by overdrank on 2007-03-10
> **nicolino101 said:**
> This is quite the conundrum. 
I've installed ubuntu dapper drake on my ibm thinkpad. It works but I can't connect to the internet using my... 
belkin wireless g card
Model # F5D7010 
compatible with 802.11b and 802.11g - whatever that means?

Someone  was trying to help me last night and gave up. I can't say I blame him. He said something about an e100 module in the kernel...  but this is all Greek to me.

I am a complete beginner when it comes to linux, but I'm actually a professional web programmer. I've run many apps on linux, just never had to set it up till now.

The card works great on win xp and win 2000 pro.

I need to get a lamp stack working and I think I could do that with internet.

Also I can't seem to get ./configure make install working. Ubuntu complains there is no such file or directory and I can't seem to find it either.

/bin holds executables... cat, gunzip, tar, etc.... correct?
./configure ...ubuntu says no such file or directory - where is it?
make... does not work.. where is it? - how do I make it work... are these executables?
I do a find... from find / make ...  and ubuntu says ... no such file or directory?

Please help before I lose the rest of my hair!!!

              Nicolino

Hi I understan how it can be installing a wireless card. I found this thread that may help you. Good luck!
[http://ubuntuforums.org/showthread.php?t=187004&highlight=belkin+Model+%23+F5D7010](http://ubuntuforums.org/showthread.php?t=187004&highlight=belkin+Model+%23+F5D7010)

---

### Post by drakan290 on 2007-03-10
I'm thinking you're going to want to get ndiswrapper. The fastest, easiest way to get the basic apps that you'd want for Ubuntu is Automatix, just google it, and there's many tutorials on how to get it to work. It'll install everything that you most likely need, and if not, you can always search google with the ubuntu tagword at the end. Have fun :D

---

### Post by nicolino101 on 2007-03-10
I appreciate the info. but I gotta tell ya. I've googled the ndiswrapper thing for hours now and the instructions are vague to say the least. I don't know how to download it without apt-get install and I don't know where it goes. I am used to download , click on it and it installs, restart and you're ready to go. This **** makes me want to dump the linux thing in the crapper.

---

### Post by nicolino101 on 2007-03-11
Well after a few days in hell, I've decided that Ubuntu is not quite ready for the Big Leagues. I know Microsoft has it's problems but, you have to admit, you'll never have to spend two full days looking for a simple driver. I still have to work with linux servers because that's my job but I think for now, my OS is going to me Windows. Hell with Zend IDE and Secure CRT I never really have to see a Linux Desktop. Who knows, maybe in a couple of years when Linux grows up, I can finally tell Microsoft to screw off.
                  Later all,
                    nicolino101

---

