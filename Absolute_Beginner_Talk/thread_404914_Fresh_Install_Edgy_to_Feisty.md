---
title: "Fresh Install: Edgy to Feisty"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Spalatum on 2007-04-09
I want to know how can I format my PC on which I currently have Edgy installed and install Feisty when it comes out. I would want to overwrite all of my data so that nothing would remain (users, passwords...). I have absolutely no idea how to do that. Take in mind that I am dual-booting with Win XP and I would like to keep that and not overwrite it. I am still new to Ubuntu and Linux in general so try to explain it as simple as possible.

Thanks in advance.

---

### Post by NikoC on 2007-04-09
Well it has been a while since I've installed Feisty, but I seem to recall that you have the option to completely format a specified partition when installing, thereby keeping your windows setup safe from deletion.

---

### Post by Malta paul on 2007-04-09
First I would backup your files in your home folder so that you don't loose them.
Then I would then run your Feisty  live live disk before mounting to your HD.
You can also use Gnome Partition manager, which can be down loaded  using Applications>add/remove. 
Only repartition your existing Ubuntu partitions, so that your windows partitions will be retained ok.
 
I am sure our forum experts can give you more help, but for now I hope this helps a little  :)

---

### Post by zvacet on 2007-04-09
If you have separate home partition and you want to keep it safe you will delete just root partition during installation proces.If you want to erase Ubuntu completly you can do it too.During installation you will came to the partition step and you will see all your partitions.Delete everything you want,and you will have free space on wich you will install Feisty.

---

### Post by indytim on 2007-04-09
If you're 100% sure you want to overwrite Edgy with Feisty when it comes out:

Via the Feisty LiveCd (install):
1.  When the install dialog comes up to the partition section, select the manual partition option.
2.  Select your existing Edgy partition as your "/" partition. (make sure you check the partition checkbox or equivalent on each of the install partitions - see below).
3.  Select your exisiting swap as same.
4.  If you're using a dedicated /home partition in Edgy and you want to do the same in Feisty, then repeat #2 for "/home".

On a new install where you want to completly rid yourself of the old ops, there is no need to do the re-format of the partition as the installer will want to do that anyways.

Good Luck,

IndyTim

---

### Post by siciliancasanova on 2007-04-09
This would also be a good opportunity to resize your windows partition if need be.  I would use the gparted live disk and you will see the partitions you have set up currently.  If you are interested in resizing and not just overwriting, you can delete your edgy EXT3 partition and resize  as you see fit, then just create a new EXT3 partition.  

Then follow the steps as listed above.

---

### Post by Spalatum on 2007-04-09
OK thanks a lot to all for the help. I will try to do what you said when I get Feisty.

---

### Post by sharealways on 2007-04-09
I tried installing the 7.04 beta fresh by deleting the partitions but it would complain about not being able to create files ..

I deleted all the linux patitions and tried it.. but did not work.. 

But the good thing was that it did not messup the exising 6.10 even though I tried to delete the partitions.. so till that gets fixed I will just wait.

---

