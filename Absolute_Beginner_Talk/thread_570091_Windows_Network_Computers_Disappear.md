---
title: "Windows Network Computers Disappear"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by samtrevino on 2007-10-07
O.k. I really can not grasp what the hell is going on with Linux here? This has happened twice now and it is more than irritating; it has me reaching for my Windows XP Pro CD. 

Issue: 

Go to Places --> Network --> Windows Network --> usually see my windows box, but now its gone, **again.**

First I am a former computer repair technician, so please understand that when I say I have not changed my configurations on either my Linux laptop or windows box and that is not the issue. The issue is my MS Windows Machines keep disappearing from Ubuntu's Networks. Strangely printing via Samba still works. This happened the first time. Unbuntu just stopped seeing any other computer on the network and I could not get it back; had to reload to fix issue. This prevents me from transferring files, with ease, between my Linux box and windows box, which is more than a huge inconvenience. If anyone else has experience with this issue please share your resolutions. The only resolution I have found is to reload Ubuntu, which is just time intensive and quite frankly I'm not going to do that again. 

Thank you,

Sam

I have reviewed several places in the forums and not found one useful solution:

[http://ubuntuforums.org/showthread.php?t=370892](http://ubuntuforums.org/showthread.php?t=370892)

did not work. was not descriptive enough to instruct on how to use "Terminal Server" or how connection was made other than using Network places. 

[http://ubuntuforums.org/showthread.php?t=299855](http://ubuntuforums.org/showthread.php?t=299855)

did not help as it was not completely applicable. 

None of these forum postings really go into depth or are very useful in trouble shooting this issue to find a PERMANENT SOLUTION! NOT A WORKAROUND! I want to be able to click on Networks and see my damn Windows' boxes, and reliably depend that this feature will not just go away after some period of time. I mean really if I wanted that kind of reliability I'd stay completely with Windows.  

What I would really like to know is how this issue developed in the first place. It appears that I am not the only one affected by it according to some of the forum posts.

---

### Post by samtrevino on 2007-10-07
Update:

Clicking on the Network file browser I can now see my Windows Machines, but I can not access them. Get error message: Sorry, couldn't display all the contents of "Windows Network: xander".

I suspect that some of the attempts to resolve this issue I applied using the "sam@laptop:~$ sudo gedit /etc/nsswitch.conf" edit appear to have worked in some limited way. However, I still can not access computer Xander. 

Thanks,

Sam

---

### Post by FRuMMaGe on 2007-10-09
> **samtrevino said:**
> O.k. I really can not grasp what the hell is going on with Linux here? This has happened twice now and it is more than irritating; it has me reaching for my Windows XP Pro CD. 

Issue: 

Go to Places --> Network --> Windows Network --> usually see my windows box, but now its gone, **again.**

First I am a former computer repair technician, so please understand that when I say I have not changed my configurations on either my Linux laptop or windows box and that is not the issue. The issue is my MS Windows Machines keep disappearing from Ubuntu's Networks. Strangely printing via Samba still works. This happened the first time. Unbuntu just stopped seeing any other computer on the network and I could not get it back; had to reload to fix issue. This prevents me from transferring files, with ease, between my Linux box and windows box, which is more than a huge inconvenience. If anyone else has experience with this issue please share your resolutions. The only resolution I have found is to reload Ubuntu, which is just time intensive and quite frankly I'm not going to do that again. 

Thank you,

Sam

I have reviewed several places in the forums and not found one useful solution:

[http://ubuntuforums.org/showthread.php?t=370892](http://ubuntuforums.org/showthread.php?t=370892)

did not work. was not descriptive enough to instruct on how to use "Terminal Server" or how connection was made other than using Network places. 

[http://ubuntuforums.org/showthread.php?t=299855](http://ubuntuforums.org/showthread.php?t=299855)

did not help as it was not completely applicable. 

None of these forum postings really go into depth or are very useful in trouble shooting this issue to find a PERMANENT SOLUTION! NOT A WORKAROUND! I want to be able to click on Networks and see my damn Windows' boxes, and reliably depend that this feature will not just go away after some period of time. I mean really if I wanted that kind of reliability I'd stay completely with Windows.  

What I would really like to know is how this issue developed in the first place. It appears that I am not the only one affected by it according to some of the forum posts.

I have the same problem.  Please post if you find a solution.

---

### Post by samtrevino on 2007-10-12
Non-functional Update and NOTICE TO OTHERS with this issue:

I am attempting to solve this networking issue since it really just irritates me to no end. Freaking networking Ubuntu Developers!! THIS SHOULD WORK OUT OF BOX AND NOT FAIL!!!!! O.k. there is my exasperated frustrated scream at the developers. FYI: If anyone knows how or if I can directly send this issue to the developers let me know? If anyone else encounters this problem and finds a solution please post. 

Thanks,

Sam

---

### Post by scrooge_74 on 2007-10-12
Are you using any firewall like Firestarter?

If so [this]("http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138") could give you and idea.

I have some of those issues before, I had to tweak the samba conf files in order to keep things working, but I have move beyond using XP systems so I don't remember exactly how i did things.

---

### Post by samtrevino on 2007-10-12
Accidental SOLUTION!!!:

WILL POST SOON!!!

---

### Post by FRuMMaGe on 2007-10-12
> **samtrevino said:**
> Accidental SOLUTION!!!:

WILL POST SOON!!!

Yay!

---

### Post by samtrevino on 2007-10-12
O.k. my solution is accidental here is what I have done to correct my issues: 

My link above [http://ubuntuforums.org/showthread.php?t=299855](http://ubuntuforums.org/showthread.php?t=299855) has some instructions to follow. Basically as follows:

Code:

sudo gedit /etc/nsswitch.conf

find this line (it may not be exactly that)

Code:

hosts:          files dns mdns

and add wins, so now it looks like

Code:

hosts:          files dns mdns wins

then install winbind
Code:

sudo apt-get install winbind

Now trying connecting to "Places->Network Servers".

Note: When I initially completed this task I could see my Windows box "Xander" but could not access it. Also when I accessed the above config file my hosts designation was complete gibberish and garbage; I'm not sure how it got corrupted, but using the winbind solution has worked. The only thing I have done differently this time is re-log (you may need to re-boot) my Windows machine and now I can see my Windows machine and access the shared folders!!!  

Let me know if this works for you. Credit goes to the link above for initiating this solution, but their issue did not resolve it completely. I'm going to continue tracking and attempting to re-create the problem to see if this solution is in fact a permanent fix.

Edit: Before I did not re-logged my Windows box and even completing the procedures above did not work. As I stated I could see the Windows box but not access the folders shared. Accessing the shared folders and the changes only worked after I re-logged my Windows XP box. 

Thanks,

Sam

---

### Post by FRuMMaGe on 2007-10-12
This seems to do the trick.  I will leave it a few days and see if it has really fixed the problem.

Looks very promising though! Thanks! :)

---

### Post by samtrevino on 2007-10-12
Watch out!

I just caught an issue that is a Windows side issue.

If your Window's box has a log-in enabled (for multiple or even one user) and/or does some kind of hibernating this could cause an error message from the Linux side not being able to find the shared folders. Linux will see the Windows box and "MSHOME" but not access any shared folders on that computer if it is not technically available on the network. 

Suggestions:

Remove log-in capacity on windows. kill all hibernating modes. Let it run. This works for me because I only use my Win XP Box  as a file dump and transfer computer. Occasionally my girlfriend will use it to surf the web otherwise it would be Linux as well.  

Side Note: You will likely have to reboot your windows box at least once every day or so depending on its in-stability.

---

### Post by scrooge_74 on 2007-10-12
I will try your solution with one piece that uses XP and logs to my Linux network

---

### Post by samtrevino on 2007-10-31
To all,

So far I have not had any recurring issues. My MS, MSHOME networks are being seen in Places -> Networks. The fix appears to be stable up to this point in time.

Sam

---

### Post by FRuMMaGe on 2007-11-01
Same

---

