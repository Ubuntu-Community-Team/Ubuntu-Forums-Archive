---
title: "Newbie - Security question"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by DoctorDruid on 2007-05-26
I have been a user of microthingy's windows for years and recently decided to look into using linux, Ubuntu was recommended to me by several people so I downloaded a distro and burned it to CD to try out. 
I don't want to go ahead and install it permanently on my computer until I get to know my way around the OS so I have just been using it directly from the CD, the only worry I have is the security.
I know that linux is more secure than microthingy's windows by default, BUT what can I do about firewall and anti-malware whilst using the live CD?
Is it safe enough to browse the net using the lie CD with no firewall since nothing is installed on my computer and therefore cannot be infected?

As I said I do not want to install linux fully on my machine until I know what I'm doing.

Also, I noticed the screen resolution only seems to go up to 1024 x 768, which is quite horrible and childish to look at after using a 1280 x 1024 res for the last few years.

---

### Post by Kobalt on 2007-05-26
You need not to worry that much about security in Ubuntu. It comes installed (even using the LiveCD) with a powerful firewall named IPtable. You don't need to set things up in a particular way (even though you can), it takes good care of this part. Viruses and malwares don't exist in Linux, no need to worry about this. 
If you want to learn more about security, read [this]("https://help.ubuntu.com/community/Security").
To adjust the screen resolution, open the Terminal up and run this ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Select the resolutions you want as available by hitting the spacebar then validate with Enter. Finally restart X with Ctrl+Alt+Backspace; and you're done.

---

### Post by DoctorDruid on 2007-05-26
Thanks a lot, I'll get on that right away. I just can't shake the paranoia instilled in me as a long time microsoft user.

---

### Post by dbott67 on 2007-05-26
> **DoctorDruid said:**
> I have been a user of microthingy's windows for years and recently decided to look into using linux, Ubuntu was recommended to me by several people so I downloaded a distro and burned it to CD to try out. 
I don't want to go ahead and install it permanently on my computer until I get to know my way around the OS so I have just been using it directly from the CD, the only worry I have is the security.

If you have a home NAT-router (for cable/DSL) then you're already behind a firewall and safe from script kiddies and probes looking for open ports.
> **DoctorDruid said:**
>  I know that linux is more secure than microthingy's windows by default, BUT what can I do about firewall and anti-malware whilst using the live CD?
Is it safe enough to browse the net using the lie CD with no firewall since nothing is installed on my computer and therefore cannot be infected?

Yes, it's safe.  By default, Ubuntu does not have any external facing services running, so you could only do harm if you chose to (i.e. downloaded & installed some nasty software from an untrusted repository.  Even so, in a live environment, nothing gets written to the hard disk, so a simple re-boot returns everything to normal.

If you choose to install to hard disk, you can install the linux firewall (firestarter/iptables), clamav (or AVG for linux), rkhunter (for rootkits).

As for the existing hard drive, Ubuntu provides you with "read-only" access to the NTFS partition (if it's mounted; otherwise any potential nasty wouldn't even know the Windows partition was there).  So, even IF a hacker COULD penetrate your system, a number of highly unlikely things would have to take place:

1. The hacker/bad guy would need to know that you're running linux (as opposed to Windows)
2. You would need to have your Windows partition mounted in a read/write fashion.
3. Any executable virus/payload would have to be marked executable by YOU.
4. You would then have to run said executable.

> **DoctorDruid said:**
>  As I said I do not want to install linux fully on my machine until I know what I'm doing.

That's fine.  The live CD is designed exactly for this purpose.  Performance can be a little sluggish if you don't have a lot of RAM, but otherwise it's a great way to learn.

> **DoctorDruid said:**
>  Also, I noticed the screen resolution only seems to go up to 1024 x 768, which is quite horrible and childish to look at after using a 1280 x 1024 res for the last few years.

Screen resolution is fully customizable.  I haven't played with it in the live environment, but if you choose to install, we can help get it set to your preferred resolution.

-Dave

---

### Post by Outrunner on 2007-05-26
> **DoctorDruid said:**
> Also, I noticed the screen resolution only seems to go up to 1024 x 768, which is quite horrible and childish to look at after using a 1280 x 1024 res for the last few years.

First, about security, I've only got to say that it is such a common concern for newcomers to Linux but the truth is, there really is nothing to worry about. There's no Linux virus 'in the wild', I guess you could say, the only concern, in my opinion, would be a rootkit, but I highly doubt you'd ever get one.

And the resolution problem is easy to solve, but that's after you install the OS. Look over this page [http://www.albertomilone.com/guides.html](http://www.albertomilone.com/guides.html) (assuming you use nvidia.). For ati, I have no idea, but I know they are very problematic...

---

### Post by starcraft.man on 2007-05-26
This [link]("http://www.psychocats.net/ubuntu/security") also is a good talk of security in Ubuntu. Theres nothing to afraid of with browsing the live CD, its completely isolated from your main OS so it can't do anything even if it got nuked by the most powerful virus out there (which, doesn't exist in wild, most viruses for linux I believe are concept and contained) >.>.

The bottom line is by using the sudo system and forcing limitations on users by default, there really isn't much a virus could do on your system unless you actually give it permission (or there is a GLARING whole in Ubuntu security, which I haven't been informed of).

Don't worry, you are safe from the BSoD and mean hackers now, Ubuntu will protect you just like a superhero :D.

Edit: geez, everyone beat me to the post. Darn ><.

---

### Post by DoctorDruid on 2007-05-26
Thanks to ALL of you for the advice, I feel better now. 

As for the performance from the live CD, I have a Pentium 4 (3.06ghz) cpu and 2GB RAM so no problems, plus even from the live CD it performs better than Vista which I have currently installed.

If I do go ahead and install it on my machine, will I still be able to retain Vista as a dual boot? I have a lot of applications (especially my 3D rendering software) that I'll still need to use.

---

### Post by Outrunner on 2007-05-26
Yes, you can dual boot, just make sure you free up some space(I think the 2nd option in the partitioning step lets you use a percentage of your Windows drive).I think you should back up any critical data you have on your Windows partition, it's always better safe than sorry!

---

### Post by dbott67 on 2007-05-26
> **DoctorDruid said:**
> If I do go ahead and install it on my machine, will I still be able to retain Vista as a dual boot? I have a lot of applications (especially my 3D rendering software) that I'll still need to use.

Yes.  My laptop is multi-boot: Ubuntu, Vista, XP Pro, XP MCE and Windows 2003 server.  All happily co-exist.  As Outrunner notes: **BE SURE TO BACKUP YOUR DATA FIRST (just in case)**.

Just be sure to install Ubuntu as the _*last OS*_ (as MS Windows likes to overwrite the Master Boot Record) which would prevent you from getting back into Ubuntu.

-Dave

---

### Post by starcraft.man on 2007-05-26
> **DoctorDruid said:**
> Thanks to ALL of you for the advice, I feel better now. 

As for the performance from the live CD, I have a Pentium 4 (3.06ghz) cpu and 2GB RAM so no problems, plus even from the live CD it performs better than Vista which I have currently installed.

If I do go ahead and install it on my machine, will I still be able to retain Vista as a dual boot? I have a lot of applications (especially my 3D rendering software) that I'll still need to use.

Do remember, linux has its own 3d software, you can find it indexed at [linux app finder]("http://linuxappfinder.com/"), in the directories.

---

### Post by DoctorDruid on 2007-05-26
> **starcraft.man said:**
> Do remember, linux has its own 3d software, you can find it indexed at [linux app finder]("http://linuxappfinder.com/"), in the directories.


Thanks for the link, some of those like blender and POV-ray I already use so thats handy, my main App is Carrara 5 pro though and only available on windows and Mac, but with the dual boot thats OK.

Again thanks everyone for the help, I'm gonna enjoy this I think.

---

### Post by starcraft.man on 2007-05-26
> **DoctorDruid said:**
> Thanks for the link, some of those like blender and POV-ray I already use so thats handy, my main App is Carrara 5 pro though and only available on windows and Mac, but with the dual boot thats OK.

Again thanks everyone for the help, I'm gonna enjoy this I think.

No problem, Linux/Ubuntu is all about having fun and being part of a community that welcomes you :D

---

### Post by carusoswi on 2007-05-26
Regarding your screen resolution while using the live CD, during the boot process, there is a screen that comes up with various options for you to choose from - one of those is to load a video driver before boot.  Highlight that option and you will be prompted to insert a cd containing your video driver.  It will take the computer a bit to load your driver, but, at some point, it will request that you re-insert the live CD, then you should be able to run at a resolution that suits you.

Caruso

---

