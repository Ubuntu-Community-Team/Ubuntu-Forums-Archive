---
title: "NVIDIA GeForce8800 Black Screen, Have Driver CD but no idea how to make it work"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by frice2000 on 2007-10-22
Ok, I know that the solution to this has been found but I am a complete and total Linux newbie so:

1.  I installed Kubuntu using the Text interface.
2. I know that the problem lies in getting the correct driver installed.
3. I boot into the recovery mode and am at the command line.
4. I have a CD with the appropriate Nvidia .run file on it.

I have no idea how to get this .run file to actually run.  I need the commands to mount the CD-ROM drive and then what the command is to run the file, or to copy it to the hard drive to run the file.  I have no idea what any of these commands are, so if someone could say what the process would be with exact commands from the root@mycomputername prompt to: 1. Mount the CD with the files on it.  2. Copy or run the .run file.  3. Any other things I need to do after that point.  When I find how to do these things online some of them work and then some don't...I have been looking for a guide on how to do this for the last few hours.

Thanks for answering my question, I am a total Linux newbie so expect that I have no idea what any of the commands would be.  I do know Windows/Mac/DOS relatively well, but again I have no knowledge of Linux.  Thanks in advance.

---

### Post by bodhi.zazen on 2007-10-22
[http://ubuntuforums.org/showpost.php?p=3269683&postcount=5](http://ubuntuforums.org/showpost.php?p=3269683&postcount=5)

Or look at envy : [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by frice2000 on 2007-10-22
Sorry, those are really too advanced for me, I don't know what I'm reading.  I have no idea how to install an application, I don't know any of the commands.  I really feel like giving up at this point, I said that I knew none of the commands.

---

### Post by Unicycle on 2007-10-22
Don't give up!  Ubuntu is easy.  Look up a simple Terminal guide in the wiki on this site.

I am fairy sure (I'm new, too) that you install .run files with this typed in the terminal:

```
cd /location of file/
sudo sh application.run
```

---

### Post by frice2000 on 2007-10-22
Problem is that the file is on a CD and I don't know how to get access to it, and then copy or run the file off of it in textual mode :P.  I honestly can't get to the CD-ROM drive no matter what commands I try.

Edit-Figured out the CD commands says that  it is not in a high enough "runlevel".  Followed the command they listed to go to a higher runlevel and the system hangs...Great.

---

### Post by frice2000 on 2007-10-22
Well thats enough time wasted, I'll try another distro.  Followed instructions linked here, and it just didn't work.  I hope I'll have more success elsewhere.  Thanks to those who helped.

---

### Post by mivo on 2007-10-22
Well, you need to be a little patient, too. :) If you use the "advanced search" of the forum and search for "black nvidia" (in titles only), you will get some links to threads with possible solutions.

My new box has a 8800GTS and the guy who built it tested it with OpenSuSE. It isn't here yet, so I have not tried it with Ubuntu, but if you do want to try another distro, this bit of info might help. (Though I will say that it is not a distro I'd necessarily use myself, but it's all Linux, really-)

Anyway, good luck, and hang in there. (But consider reading the other threads about this problem.)

:)

---

