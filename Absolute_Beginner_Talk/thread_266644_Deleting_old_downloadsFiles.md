---
title: "Deleting old downloads/Files"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by IusedTObeSOMEONEelse on 2006-09-27
Question is regarding downloads. I have downloade some linux os's to burn. Among downloading other thing, I want to free up some RAM and how mdo I find whats taking up RAM space and get rid of it. Please be mind-full that I'm "Not the brightest bulb on the tree" so please give me simple terms. But I am enjoying this learning exp. and I have not crashed the box in about a week!!

---

### Post by bswilson on 2006-09-27
Let me try to help.  Nothing is installed into RAM.  You can't free up more RAM by deleting programs.  Programs are installed on the hard drive.  If you are trying to get more space on your hard drive, you should uninstall the software packages that you don't need (use the Synaptic tool).

If you're saying you really want or need more RAM, then you should buy some.

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
Is there some thing I can type into terminal to get what ever is eating space and tells how much space there is? Thanks for reply

---

### Post by Perfect Storm on 2006-09-27
Well, if you used synaptic/apt-get/aptitude alot you could try this:
```
sudo apt-get clean
```

---

### Post by bswilson on 2006-09-27
> **MustangSallydd said:**
> Is there some thing I can type into terminal to get what ever is eating space and tells how much space there is? Thanks for reply

Uh, not that I know of.  You can enter this command to tell you how much free space you have on your disks:

```
$ sudo df -h
```

I'm not aware you can do anything to show space used on a *per-program* basis...

---

### Post by uk_sphinx on 2006-09-27
whenever i have to explain ram and harddrive space to my brothers or family etc..
i always think it is best to explain to them like this.
think of it as a human brain...
ram is used as short term memory
hard drive is used as long term memory
ram holds little info that say a program needs to remember but will be deleted after a short while once the program has no need to remember it anymore.
the harddrive is for actualy storing large amount of data for long periods of time
i know this dosnt help your problem but it is a good idea to learn the differance as it is a big part of learning computer systems and the way it works.

---

### Post by jimbren on 2006-09-27
you can use du to find out about your disk space usage.  There's also a program called durep that's available in the repositories that will give you the same type of information in HTML format so you can easily browse the directory tree.

Here's an example of what i do:
```
cd /
sudo du -h >/home/jim/usage.txt
```

change to the root directory so you get the whole volume, then use sudo because oherwise you won't have permissions on most of the directories. the -h switch stands for human readable, which will put the sizes into giga and megabytes instead of kilobytes, then you output the whole thing into a text file that you can easily read and scan through.

with durep, you would do something like this, again from /.
first, make a directory in your home directory for the output.  the program will generate over 100 .html pages, so you want to ave someplace to put it all.
```
mkdir diskusage
cd /
sudo durep / --webdir=/home/jim/diskusage
```

then just browse to the directory and open up the first web page.

You might want to read the man pages for either program--I'm not at home and can't remember the exact syntax.

Hope this helps.

jim

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              37G  4.5G   31G  13% /
varrun                125M   88K  125M   1% /var/run
varlock               125M  4.0K  125M   1% /var/lock
udev                   10M   96K   10M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   18M  107M  15% /lib/modules/2.6.17-10-386/volatile             Could you please explain this and whether it'good or not? I believe I have 256 RAM

---

### Post by uk_sphinx on 2006-09-27
learn the differance between ram and hard disk space
your gonna confuse yourself
try google if you cant understand what i said

---

### Post by nts on 2006-09-27
I always use:

RAM is like your glovebox - quick to access, but no much room

HDD is like your boot(or trunk ;)) - slow to access, but more room

Very loose definition, i know - it works on my computer iliterate friends/family.

---

### Post by Metacarpal on 2006-09-27
Hi Sally,

Are you trying to clear out space that was used up when you downloaded files to your computer?  If so, that's your hard drive (sometimes also called a hard disk or HDD).  RAM is something else entirely, which your computer uses to store data for programs that are actually running at the time.

If you're looking to clear up space from things you downloaded, then how to get rid of it depends on how you downloaded it.  You were talking about downloading Linux OSes to burn (to CDs?)... in that case, after you burn them, all you have to do is find the file you downloaded (probably on your desktop), drag it to Trash, and empty the Trash.  But you still have about 85% of your hard drive free, so it shouldn't be affecting you.

If you need more RAM (memory used to run programs), that's a little trickier.

If worse comes to worst, I live in NYC too and will be glad to help you out.

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
Thanks every one! I'm all set on this one. I think I may need to just put another stick of RAM in there. It's just that some times things are a bit slow and I use a High-Speed connection. Thanks.

---

