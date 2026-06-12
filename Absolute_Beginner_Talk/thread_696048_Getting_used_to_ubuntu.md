---
title: "Getting used to ubuntu"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Tek-Noir on 2008-02-13
Im still getting used to using ubuntu but my brain is still thinking in windows lol.
Ive just a few other questions and hope someone could answer them.

1. Do you need to defrag regularly and if so what would be the best way of doing this?

2. I used to a system clean on windows quite often to keep things running fast do i need to do this on ubuntu?

3. When removing programs dose ubuntu does it leave old files about like windows used to?

4. Should i be using antivirus software and if so what would be the best one.

Thats all i can think of at the minute, im sure they'll be more. lol

---

### Post by chewit on 2008-02-13
1) No you don't need to defrag, EXT3 does a good job keeping it together. I believe it does a mini defrag every 25-30mins

2) No there is no need for a system clean. [But i found this tutorial helpful.]("http://ubuntuforums.org/showthread.php?t=140920&highlight=clear+rubbish")

3) Yes, it does leave the installer, the tutorial shows you how to get rid of them.

4) Linux have no viruses in the wild, don't worry about them! Save RAM, no need for virus scan!

---

### Post by smacattack on 2008-02-13
1. No you don't have to defrag.. assuming you are using a ext* partition system which doesn't fragment itself to begin with.

2. You can create a /home partition to keep all of your configuration files and reinstall the system whenever you choose with little consequence (assuming your data is backed up) but I imagine you won't find it slowing down much over time as Windows tends to.
(more here [www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome))

3. Ubuntu doesn't hang on to old files as badly as Windows does but it does happen. If you install a program using 'sudo apt-get install', i've found a good way to remove it completely is 'sudo apt-get remove --purge' followed by the program. I believe the option 'completely remove' when you check a program in Synaptic Package manager does the same.

4. Antivirus you don't need to worry about, as far as I'm concerned but if you do want one I know one ive heard of is called clam (just search is synaptic if you wish) but really, you very likely won't need it. What most people would suggest is making sure you have a firewall intact to protect yourself, I know the default one is called Firestarter so you might want to look further into that if you're worried. But overall, Ubuntu and Linux in general is much more 'secure' from virus', but of course, it can never hurt to be too cautious.

Regards.

smac

---

### Post by Ek0nomik on 2008-02-13
> **Tek-Noir said:**
> Im still getting used to using ubuntu but my brain is still thinking in windows lol.
Ive just a few other questions and hope someone could answer them.

1. Do you need to defrag regularly and if so what would be the best way of doing this?

2. I used to a system clean on windows quite often to keep things running fast do i need to do this on ubuntu?

3. When removing programs dose ubuntu does it leave old files about like windows used to?

4. Should i be using antivirus software and if so what would be the best one.

Thats all i can think of at the minute, im sure they'll be more. lol

1.  No.  Here is some further reading for you:

[http://ubuntuforums.org/showthread.php?t=383100](http://ubuntuforums.org/showthread.php?t=383100)

[http://ubuntuforums.org/showthread.php?p=2294941](http://ubuntuforums.org/showthread.php?p=2294941)

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

2.  Assuming you haven't manually added programs to start when you load up the computer, your computer should always run as fast as it has in the past.  Software in Linux only runs when you tell it to.  It doesn't just start on load like some of the software written for Windows will.

3.  Depends...  If you install something from Synaptic or you install something using apt-get in the terminal, it will keep the configuration settings.  (They are almost always stored in /home/yourUserName/.programName)

4.  You don't need anti-virus software for Linux as you will find it hard to find a virus that will run on Linux.  Nearly all viruses are built for Windows machines, so you don't have much to worry about at all.  Also, all ports in Ubuntu are closed by default, so your computer is shut off from the Internet unless you install a program that is going to listen on a certain port.

---

### Post by jken146 on 2008-02-13
Hi there, and welcome to Ubuntu!

> **Tek-Noir said:**
> 1. Do you need to defrag regularly and if so what would be the best way of doing this?
There's no need to defrag an ext3 file system (that's the one Ubuntu uses by default).  I'm not entirely sure why this is -- I think it has to do with something called the 'journal' -- but you just don't defragment it.  However, every 30 or so boots, there will be an automatic check of the filesystem, which doesn't require you to do anything (booting will just take a bit longer).

> 2. I used to a system clean on windows quite often to keep things running fast do i need to do this on ubuntu?
There is no equivalent of that in Ubuntu, and it's unlikely that you'll notice a drop in performance over time, through normal use.  That said, here's a howto: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

> 3. When removing programs dose ubuntu does it leave old files about like windows used to?
Some things do get left behind occasionally by the package management system -- see the link I just gave you.  In addition, packages you download are kept in /var/cache/apt -- not sure how long for though.  Using aptitude rather than apt-get to install and remove things seems to help with this.

> 4. Should i be using antivirus software and if so what would be the best one.There aren't any Linux viruses out in the wild, and so the only point in using anti-virus software would be to check if you're sending Windows viruses on to other people.  This is important for mail servers, but really not a concern for desktop users.

Thats all i can think of at the minute, im sure they'll be more. lol[/QUOTE]

---

### Post by Tek-Noir on 2008-02-13
Brilliant, thank you all for the help. Thats me fully migrated from windows and couldn't be happier :)

---

### Post by littletinman on 2008-02-13
Those are all reason's why Ubuntu is so far superior to windows.

---

### Post by cybertron3000 on 2008-02-13
I agree with littletinman above, this operating system is the best by far.  My Ubuntu also uses an average of 17%MB RAM, versus the 35%MB RAM used on the "fast" Windows XP.  I have 750MB by the way.

---

### Post by stchman on 2008-02-13
> **Tek-Noir said:**
> Im still getting used to using ubuntu but my brain is still thinking in windows lol.
Ive just a few other questions and hope someone could answer them.

1. Do you need to defrag regularly and if so what would be the best way of doing this?

2. I used to a system clean on windows quite often to keep things running fast do i need to do this on ubuntu?

3. When removing programs dose ubuntu does it leave old files about like windows used to?

4. Should i be using antivirus software and if so what would be the best one.

Thats all i can think of at the minute, im sure they'll be more. lol

1.  No EXT3 does not fragment like NTFS or FAT32

2.  No, but you can use this.  [http://www.stchman.com/cleanup.html](http://www.stchman.com/cleanup.html) to remove old cached packages.

3.  No, since Edgy using the autoremove on apt-get removes all UNUSED dependencies.  The Synaptic package manager is a great thing.

4.  The viruses and spware running around in the wild are targeted for Windows.  They have no effect on Linux.  You can install an AV to keep you from emailing an infected file to your Windows friends.

---

