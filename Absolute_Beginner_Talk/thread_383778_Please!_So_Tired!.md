---
title: "Please! So Tired!"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-13
Trying to install Ubuntu at last! BUT it says this to me:

The ext3 file system creation in partition #1 of IDE1 master (hda) failed.

What to do? I've had problems after an other... can't wait till this is all fixed!

Thanks for the help!

---

### Post by taurus on 2007-03-13
Is there anything on /dev/hda?  Are you using the LiveCD or the alternate CD and which release are you using, Dapper or Edgy?

---

### Post by bulldog on 2007-03-13
Are you trying to make a dual boot with windows,or just ubuntu on the whole disk.

You have to provide some extra info about your problem.

In the mean time it could be a good idea to download and burn the GParted live cd [30MB]
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Boot from the GParted live cd and you'll have a graphical partitioner which is much easier to use.

Create a 10GB partition and format it as ext3
Create a 1GB partition and format it as swap
Create a partition as big as you like for your /home folder and format it as ext3

If done exit the gparted live cd and pop in the ubuntu cd.
If you come to the partition part,choose manual partition,you already did this.
Mount the 10GB partition as  /  (root)  and format it again as ext3
Mount the 1GB partition as swap and format it as swap again
Mount the last partition as /home and format it ext3 again.

Continue the install and all should go fine.

Good luck,and if you have more questions just ask here on the forums.

---

### Post by julie_lebou on 2007-03-13
Well, i dunno if there's something on hda cause I can't click on i'm using the live cd... witch version, I'm not sure cause it's been a few months that I burned this, and i'm not doing a dual thing, I just want Ubuntu.

---

### Post by bwallum on 2007-03-13
Hi Julie

First check your install disk is ok. This is an option shown when you boot up with the live CD.

If the Live CD is ok and you are happy that the install went ok, then shut your machine down and go into your computers setup when you restart. (Typically this is by pressing the Del, Esc or F2 key a couple of times as the computer boots. 

If you get a simple setup screen you have done this correctly. Navigate to where your hard drive(s) is(are) defined. Auto detect the hard drive if you have that function. If not change the setting then return it to the 'auto' option. Look to set if you can save the Master Boot Record (MBR). If you can press the save MBR option.

Then exit and save the settings. Remove the install CD and let your computer reboot. Hopefully you will then boot Ubuntu from the hard drive. If not you will have to use the CD and this time when offered the start up menu choose the start from hard drive option.

I had similar problems last week, I'm a newbie so please take my advice as such.

Kind Regards
Bob

---

### Post by julie_lebou on 2007-03-13
but if i do this, will my hard drive be erased? I want to do a restore as well, my computer would be faster I suppose.

---

### Post by julie_lebou on 2007-03-13
went to my computer settings.. didnt find anything to do there... and if i try to boot from drive it dosent work.. could somebody help me to install ubuntu on my computer? :( I cant wait to have it!

---

### Post by lamalex on 2007-03-13
also do a hard drive check in your BIOS. maybe your hdd isn't in top condition. I've had that problem before when it couldn't format my hard drive because a bunch of the sectors were damaged.

---

### Post by Guinness Bug on 2007-03-13
> **julie_lebou said:**
> went to my computer settings.. didnt find anything to do there... and if i try to boot from drive it dosent work.. could somebody help me to install ubuntu on my computer? :( I cant wait to have it!

I had the same problem when I installed ubuntu. I just used a lot of swearing, had a Guinness, and deleted my entire hard drive to install ubuntu. To be quite honest, I'm glad that I did. You may have to do the same thing I did. (Erase the hard drive- not swear and drink Guinness- although I do recommend the Guinness! :) )
Please remember that I am a newbie- just trying to do good things for people!

---

### Post by julie_lebou on 2007-03-13
but what do you meen erase my hard drive? how do you do that?

---

### Post by perce on 2007-03-13
I had a similar problem with Edgy, and my installation failed several times. Then I tried with the alternate CD and it finallly worked. If I remember correctly, for some bug you aren't ablle to install in an existing partition, so when you try with the alternate CD you should repartition the disc. I have no idea why it worked for me, and if it will work for you. Also, a 10 GB partition for / seems quite a lot to me, if you are going to have your home in a separate partition.

---

### Post by Guinness Bug on 2007-03-13
> **julie_lebou said:**
> but what do you meen erase my hard drive? how do you do that?

When using the live cd (not as an install) you have the option of installing ubuntu permanently. During that install, you are given the option of erasing your hard drive and letting ubuntu install itself, creating the partitions yourself, or letting ubuntu make it's own partitions. I tried to make my own partitions, and that didn't work, so I tried to let ubuntu make it's own partitions- that didn't work. Only after I chose to delete the entire hard drive did I get to the point I am now. I am still learning, though- so please remember that.
I really hope that you we can all get this fixed for you.
Best of luck!

---

### Post by Skidpad on 2007-03-13
> **julie_lebou said:**
> but what do you meen erase my hard drive? how do you do that?

Here's a visual guide to the Edgy installation: [Clicky here](https://help.ubuntu.com/community/GraphicalInstall)

You will see the particular steps where you have the option to erase your entire hard drive

:)

---

### Post by julie_lebou on 2007-03-14
worked, thanks guys!

---

### Post by desiretosee on 2007-03-14
I think there are lot of program can be used to erase the partitions of your hard disk.
what you neek is another healthy computer of your family or friends. connect your hd to their computer with hd holder, which you can borrow from your friends or buy one in the computer accessories shops.(very cheap, 15 $ mayby 2 -3 bucks more) .
Or even better if your friend is so kind, open his desktop computer to connect your hd with IDE interface.(you have to switch a small bar on your hd, to set it as slave hd)(this method can only be used when you are not using notebook, with note book, you have to use the first method)

then you can copy important informations or files in the computer of your friends(temperarily, with an folder with your name. After that, you can erase all the parition of your hd. with power partition magic(name of program) version 8.0 or any partition manage software you can find (free or commercial). then take your hd out. connect again to your own computer. start with the Ubuntu CD or dvd in the rom. take a cup of coffe and a bag of cornflake.
Enjoy you installation of your Ubuntu. (dont forget to copy your files back from your friend, if you have private informations, you'd better set a password to prevent easy open of your folders.)
warm regards

---

### Post by bwallum on 2007-03-15
Could you tell us what you did to get it working please? Detail would be great but don't worry if you can't remember it all. Just tell us roughly how you solved the issue of getting Ubuntu up and running. (I'm trying to add some newbie stuff to Wiki, hence the request)

Kind Regards
Bob

---

### Post by julie_lebou on 2007-03-15
Ummm i didn't do much, what happened is that i just tried again to install ubuntu with the first option where you can decide with the horizontal line how much space to use, instead of using the erase disk option like i was trying to do before. Both option didnt work before, but suddenly, it was working for the first time.. the only thing, the installation CRASHED! So there i was really frustrated...  when I went to try back, the first option was not even there anymore! GRRR... there was only erase disk and manually.. so I chose erase disk, and it worked! I dunno why, it's really weird, but that's what I did! LOL

---

