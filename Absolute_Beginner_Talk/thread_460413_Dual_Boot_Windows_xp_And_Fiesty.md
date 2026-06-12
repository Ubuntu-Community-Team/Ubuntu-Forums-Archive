---
title: "Dual Boot Windows xp And Fiesty"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by charlie1992 on 2007-05-31
I have just installed Ubuntu on the same  hard drive as windows. I let ubuntu partition itself in the free space on my hard drive.  Now, when I turn the computer on, it give me a choice of OS.  If I choose windows, It starts to load up then shuts down and restarts again.  If upon the restart I choose Ubuntu it works fine if I choose windows the cycle starts all over again.  Can anyone help, I am very new to Ubuntu.

---

### Post by jd65pl on 2007-05-31
Do you get an error message or similar? At what point does it restart. Do you see the Windows XP logo boot splash?

---

### Post by charlie1992 on 2007-05-31
Thank you for replying.  No, No error messages.  It will get as far as seening the windows logo, then the little bar starts to go across.  Then it stops.

---

### Post by jd65pl on 2007-05-31
Can you try to boot in safe mode in windows?? i think its ? F8 at boot.

---

### Post by Atomic Dog on 2007-05-31
> **jd65pl said:**
> Can you try to boot in safe mode in windows?? i think its ? F8 at boot.

F8 should do it.  Select the plain Jane safe mode and see what happens.  Sometimes just booting into safe mode straightens things out (I have no idea why).  There are other repair options for WinXP, but try safe mode first before trying to restore from a previous restore point.  Seems very strange that you would have this type of issue.

---

### Post by hank hill on 2007-05-31
hi, i just installed ubuntu also ,and had the same problem .So i did a search and found this video
	
Ubuntu Linux / Windows Dual Boot Instructional Video ...just google that thru explorer and watch it (14 minutes)
it shows how to do a fresh install of xp and create a partion for windows then using the textbase installer (alternate cd ,not the live cd)make the swap and other primary partion.There are a few things to pay attention to tho so watch the vid.
You will need to download the alternate cd though ,by putting a check mark in little box on ubuntu download page.It seems the live cd trys to put everything on 1 partion and windows wont boot.
I have messed around w/linux suse 9.1 and then suse 10.1 x64 and could never get the dualboot to work letting linux do the partioning so i always went back to windoze, but now w/ubuntu and watching that video I am runnin dual boot just fine and i luv it(ubuntu) if i could figure out how to run n2k3 thru wine i'd get rid of windoze alltogether.
If u have prob.pm me i will help u!
sorry for lenghth of post but i'm very excited to finally be running linux!!!

---

### Post by openmtl on 2007-05-31
> **charlie1992 said:**
> I have just installed Ubuntu on the same  hard drive as windows. I let ubuntu partition itself in the free space on my hard drive.  Now, when I turn the computer on, it give me a choice of OS.  If I choose windows, It starts to load up then shuts down and restarts again.  If upon the restart I choose Ubuntu it works fine if I choose windows the cycle starts all over again.  Can anyone help, I am very new to Ubuntu.

This isn't a Ubuntu problem but a "Windows" problem.

Did you resize the Windows partition ? If so then Windows MUST check the integrity of the file system at least once after resize. On NTFS I've usually had no problems with re-size and on the first Windows boot after a resize  it goes to a Blue DOS-like screen to do the NTFS file system check. Something may be upsetting Windows on file system check so badly that it wants a human to confirm what to do. Try booting Windows in safe mode.

Did you shift the Window partition around i.e. insert another partition before the /dev/hda1 thus upsetting how Windows knows the drive letters ? The boot loader in Windows will go quite far until it tries to find things like pagefile.sys on a specific partition and then it borks.

---

### Post by hank hill on 2007-05-31
oh ya ,i tried  getting windoze back all day yesterday with recovery console ,using fixmbr,fixboot ,etc.
none of it worked.
it was the same exact prob ,first it would show black screen w/the words starting up ,and would freeze .this when i tried to boot to windoze,so i tried the i-386 insteead of the amd64,then it would just start back up to post evrytime, im tellin ya that video will show ya wat works,i just couldnt copy the link to it cuz it is in some new google videos.

---

### Post by hank hill on 2007-05-31
i also tried safemode ,wouldnt boot.
are u using an xp pro disk
?

---

### Post by northicert on 2007-05-31
jd65pl,  Hang in there.  Charlie seems to be having a problem that I see quite often in these threads and the same reason I still boot live cd.  Hope you find the answers.

---

### Post by hank hill on 2007-05-31
what im trying to say is i have no prob now ,ubuntu & windows is working fine dual boot.But i had the same prob. as charlie 1992 . windoze needs its own partion! 
and then it will work!

watch the video......

---

### Post by northicert on 2007-05-31
I assumed fiesty install would do that automaticaly without messing win XP up.   Sorry to hog you thread Charlie

---

### Post by charlie1992 on 2007-05-31
Running windows in "safe mode", produces for a long list of error lines.  The word partition comes up in almost every line. Should I just reinstall windows.  Can't even get to a c-prompt or anything else in windows to try to fix it there.

---

### Post by MindFork on 2007-05-31
I'm downloading Ubuntu Live and  I will be testing it on my folding rig as a dual boot.  In order to take it "prime time" on my main computer, I am going to have to be able to get a dual boot to work right off the bat.  Having to do a clean install would mean having to completely set up my windows install from scratch, AND get Ubuntu going.  

Hopefully I won't have this same problem...

---

### Post by northicert on 2007-05-31
I would read whats on LinuxDevCenter.com first.

---

### Post by Shazaam on 2007-05-31
> **MindFork said:**
> I'm downloading Ubuntu Live and  I will be testing it on my folding rig as a dual boot.  In order to take it "prime time" on my main computer, I am going to have to be able to get a dual boot to work right off the bat.  Having to do a clean install would mean having to completely set up my windows install from scratch, AND get Ubuntu going.  

Hopefully I won't have this same problem...


You shouldn't unless you delete any backup partitions and such with a name brand PC. Do a defrag first in Windows, reboot with the Live/CD, use the livecd to shrink the Windows partitions, and install Ubuntu on the unformated space. I have installed Ubuntu on less than 5 gigs and it WILL run. 1gig for /(root), 500meg for /swap and the rest for /home.
Look at this-- [http://www.shell-shocked.org/article.php?id=230](http://www.shell-shocked.org/article.php?id=230)

Sorry for the hijack.

---

### Post by northicert on 2007-05-31
Good luck and hope all goes well.  I have a second hard drive and I'm still hesitating about the install with so many XP not working threads.

---

### Post by MindFork on 2007-05-31
I couldn't get the ubuntu partitioner to shrink the windows partition, so I just did a clean "guided / entire disk" install of ubuntu, since the only thing installed on this PC is folding @ home and a firewall.  

Ubuntu will probably never go on my main rig, but if it works like a champ on my other one, I can migrate myself slowly to the ubuntu machine with the xp computer as my back up.

---

### Post by northicert on 2007-06-01
I think you'll like it better this way for now.  I would but I'd have to get another used computer to do this and the wife would protest to that big time.  Oh Well!!

---

