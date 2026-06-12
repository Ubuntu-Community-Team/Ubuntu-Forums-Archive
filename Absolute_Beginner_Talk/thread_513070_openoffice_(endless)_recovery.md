---
title: "openoffice (endless) recovery"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Knoob on 2007-07-30
when i start openoffice it crashes and then it goes to recover the file, says file is successfully recovered, but when it reloads it, it crashes again and starts to do recovery again, and so on repeating endlessly. (well until i cancel the process).

i am using openoffice 2.2 in Ubuntu Feisty 7.04.
this doesn't happen with openoffice writer (it happens with calc and draw)

i've tried doing the following:
```
mv .openoffice.org2 .openoffice.org2_BACKUP
```
and then restarting openoffice.
but same results of crash and recovery.

i've also reinstalled openoffice.org in Synaptic, but same errors occur.

i've also done
```
sudo aptitude reinstall openoffice.org
```
still no luck.

any other suggestions?

---

### Post by 5-HT on 2007-07-30
I've had that happen before and managed to get everything working again by asking open office to not recover the file (everything in the file was there from the last save point). Hard to tell whether it's the same issue or just similar symptoms though.

---

### Post by Knoob on 2007-07-30
> managed to get everything working again by asking open office to not recover the file
by this do you mean just clicking cancel in the recovery window?
when i do that it goes to open a new document in openoffice writer.
if i then open a file in openoffice calc, it crashes again and same cycle happens.

oo writer seems to be okay. crashes only happen in oo calc.
i reinstalled oo calc in synaptic, but i'm still having the same problems.

other ideas would be very much appreciated.

---

### Post by tprzepiorka on 2007-07-30
I can't help much with getting OO to work. However, I suggest using AbiWord. I prefer it to OO because it is faster and works just as well.

---

### Post by Knoob on 2007-07-30
problem was solved with the help of isaacj87 over at qunu.com
i'll summarize what we did so others may benefit from it if they have same issues.
(sorry the exact commands escape me as we did this yesterday)

the problem was mainly due to a corrupted file during the automatic upgrade of openoffice.
debian package for openoffice.org-common was somehow corrupted.
so what we did was
1. completely remove openoffice.org (from synaptic)
2. made a backup of the corrupted debian package (just in case)
3. removed the corrupted debian package
4. update
5. reinstall openoffice.org (from synaptic)

now everything works well.

---

### Post by hollowhead on 2007-07-31
I had this problem with a paper I was writing.  I cut a image from one point to paste to another and oO write crashed.  Recovery didn't work or at least went on forever.  I'd made lots of small text changes.  After trying to open several times I remembered I had abiword and that this opened write files.  It lost the graphics but recovered all my text.  It wouldn't allow me to save the file in any format but I managed to past text into another empty file recover form backup my original paper file in oO and paste the text back in.  Moral keep a backup.  When I first upgraded to fiesty oO was unreliable.  It has become reliable.  I've increased oO's memory allowance and set the Java correctly for graphics for some reason this was not setup by the upgrading software.  The only thing that is unhappy is impress at editing files in powerpoint format.  Hope this helps.

---

### Post by Hagar Delest on 2007-08-01
You should install the official version, see here : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

### Post by procciv on 2007-08-06
I had the same problem with calc and when I started the solution proposed by knoob, I noticed  that openoffice was not installed but only the components.  It seems that the default installation do not install ooo.  I only installed it via adept and it now works perfectly.

I hope this will help.

---

### Post by ezphilosophy on 2007-08-20
I just wanted to say that I had nearly the same problem as the OP.  I was surprised when I did a search in the forums that this was the only thread that came up!

Openoffice was continually starting the document recovery laucher for writer and I couldn't open any documents.  Like the OP did, I completely removed openoffice (via adept since I'm running Kubuntu) and reinstalled the full suite.

It seems to be working fine now.

---

### Post by beanco on 2007-10-23
having a similar problem with writer, keeps wanting to go to documetn recovery and then does not do anything... I did not have any document that I ant to recover.

how to remove the entire suite in the terminal rather than using synaptic ( I do not like synaptic)

thanks

robi

---

### Post by beanco on 2007-10-23
so i remvoed and reinstalled using synaptic but i still get the same annoying error and I cannot open writer.

any ideas?

thanks

robi

---

