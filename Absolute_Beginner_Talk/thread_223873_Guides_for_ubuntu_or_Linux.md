---
title: "Guides for ubuntu or Linux"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Ausus on 2006-07-27
Hi All,

Could someone please point me on "How to Guides in Linux".
I think this is the most common problem, when trying to use Linux for the first time.
Unix or linux is ver cryptic, this is why many shy away.
So please point me in the right direction.
Are their any ubuntu Linux user groups in Gauteng South-Africa,who I might be able to contact or meet on a regular basis.

:?: 
I'm current using WinXp64 Prof. edition, and would like to dual boot.

Regards

Ausus

---

### Post by disciple on 2006-07-27
hey ausus
welcome! 

before you fully install, you should make a list of your hardware, and do a search to see their compatibility with linux.. (you can check on this forum)  i.e. video, wireless, etc..

personally, once video and wirelesss ( or any net connection) is up, i can move from there

secondly, have you downloaded a livecd? this will allow you to get your feet wet without fully committing, if you arent exactly comfortable


anyhow, in answer to yor question, there is an extensive HOWTO section right here on the forum's first page , under Support and Resources that should cater to many needs

when setting up, i use [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)     to assist in configuring stuff like multimedia, third party apps, windows compatibility etc


with regards to south african linux groups, i am unaware of any off hand, but i am sure they are there :-)   failing that, you always have these forums  :-)

good luck

---

### Post by Ausus on 2006-07-27
Hi Disciple,

My Hardware:
Ausus A8N32 SLI mobo.
nVidia mobo chipset drivers.(nVidia C51D and CK804 SLI)
Dual core AMD CPU
Realtek 850 onboard sound.
Siltek 3132 SAT as well Raid drivers.
Sata nVidia drivers
Raid nVidia drivers
USB from nVidia chipset.
Hp Printer Cli 975cx

How do you go about looking for the above hardware compatibility.
I know their is a vast information on the Internet, but to get to the answers in quick time.

Reagards

Ausus
:smile:

---

### Post by Sef on 2006-07-27
> How do you go about looking for the above hardware compatibility.

Best way to check for compatibility is get the livecd and run it.  If you have a problem with the livecd, almost certainly you will have the same problem on an install.

[South Africa Download]("ftp://ftp.is.co.za/linux/distributions/ubuntu/releases/6.06/") (go to  ubuntu-6.06-desktop-amd64.iso or
ubuntu-6.06-desktop-amd64.iso.torrent)

As for the Linux Users Group, [click here.]("http://www.glug.org.za/")

---

### Post by disciple on 2006-07-27
wel it seems that your board may have trouble , with regards to keeping an existing RAID setup ( which i would assume yes, since you want to dual boot with XP)

it stems from the fact that apparently, the board's  nvidia RAID is not a full hardware implementation; rather, it relies on software to do the job

anyhow, that's IF you have a raid set up....

the below HOWTO may help..
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

you didn't mention your graphics card, but you'll have to do some extra work in order to get the very latest drivers up and running. Nvidia cards seem to be supported much better than ATI cards , at the moment

( both are closed source drivers that you'll have to download apart from your cd install, and do a fair amount of tweakin to enable.. covered in various HOWTOs)
 
in the guide i mentioned in an earlier post, there are instructions on how to install the regular Dapper drivers ( both ATI and Nvidia)


i've never set up printing in linux, so i can't tell you off-hand if it is a headache to set up :-)   but it sounds like it..  

the livecd , as mentioned by sef, is a good test of compatibility, so try it out..
don't forget to  backup all your important data to another machine, or a dvd or something, before you do the full install

---

### Post by tturrisi on 2006-07-27
Ubuntu Guides:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
[http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[http://www.ubuntu.com/support/faq?action=show&redirect=FAQ](http://www.ubuntu.com/support/faq?action=show&redirect=FAQ)

---

### Post by justicerulesok on 2006-07-27
> **disciple said:**
> 

i've never set up printing in linux, so i can't tell you off-hand if it is a headache to set up :-)   but it sounds like it..  

I'm a complete n00b but I got network printing up and running within a hour of first install - piece of cake.

I also think the two things to worry me would be graphics (so i can see what I'm doing) and network/web connection (so I can get nice forum people to help me fix stuff).

download anything you may need first & then get ready to rumble. :-)  goodluck & enjoy.

Justice.

---

### Post by Ann667 on 2006-07-27
I'm very new to linux as well.  The first thing I did was poke around these forums a lot until I got my basic questions and concerns sorted out, like security and whatnot.  (I also have the good fortune of having two linux savvy brothers who are only an email away, one of which used Ubuntu, and who could give me a few starter pointers.)  

From the perspective of a completely new user, I have to say I really like Automatix.  Once I got the basics sorted out to be up and running, which wasn't difficult, I found a link somewhere in these forums for an online tutorial for linux (not dist specific).  Here's the link. [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)  I haven't gotten very far with it just yet, but so far I really like it.  (maybe one of the experienced users here could give the link a quick check and give it a “good” or “bad” as I'm not experienced in the way of linux just yet and can't give a truly objective opinion.)  But from the perspective of a completely new user, I find it easy to follow.  (Although I believe there are some Ubuntu specific ways of doing things that might not be covered.  [I haven't gotten that far with it yet, so not sure.]  Especially since the root account is locked by default and we have to use “sudo” instead.. ? <-- someone who actually knows what they are talking about may need to correct me there.)  

Anyway, I hope that helps a little.  I can't give any real advice, but I can give opinions from the perspective of a new user.

---

### Post by Drakkor on 2006-07-27
Here is a great all in one guide I just stumbled upon:
[http://www.futuredesktop.com/ubuntu6.06.html](http://www.futuredesktop.com/ubuntu6.06.html)
As for HP printers,my HP was a breeze,but you can check here:
[http://www.linuxprinting.org./printer_list.cgi?make=HP](http://www.linuxprinting.org./printer_list.cgi?make=HP)  :p

---

