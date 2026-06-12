---
title: "Clam AV virus definitions"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-08-21
Hmmm... I wanted to install and run Clam AV on my computer, but don't seem to have any virus definitions.  I began by using Add/Remove to install "Virus Scanner", the graphical front-end to clam.  Then:

When I ask Clam to scan my home directory, it says, "You do not appear to have any virus definitions!  Running freshclam -v at root may fix the problem."

"sudo freshclam -v " warns me that my version of Clam is outdated.  I have version 0.90.2, and the recommended version is 0.90.1 (?).

"sudo freshclam" gives the same result.

"sudo apt-get install clamav-freshclam" informs me that I already have the newest version.

If I try to use the Clamtk GUI, and click on Help > Update Signatures, I'm informed that to do so I have to be logged in as root.  In all honesty, I don't remember how to log in as root.

When I first installed Virus Scanner, I got a couple of error messages.  Since it didn't seem to work, I uninstalled it and restarted the computer.  Then I reinstalled it.  I'm still having problems.

Help?

---

### Post by gkey on 2007-08-21
1st - to run virusscanner in graphical mode as root enter " sudo clamtk" in a shell.

for your other questions: have a look at this page on the wiki:
[https://help.ubuntu.com/community/ClamAV]("https://help.ubuntu.com/community/ClamAV")

---

### Post by Mr. Svinlesha on 2007-08-21
Thanks, **gkey**.

When I try to run "sudo clamtk" I get the following line response:

> LibClamAV Error: Database Directory: /var/lib/clamav/ not locked
connect(): No such file or directory

The Virus scanner GUI starts, but I still get the same error messages.

Suggestions?

---

### Post by Mr. Svinlesha on 2007-08-21
Bump!

---

### Post by ddrichardson on 2007-08-21
Try: ```
sudo service freshclam stop
sudo rm -Rf /var/lib/clamav
sudo service freshclam start
sudo freshclam
```

It looks like you may have to re-install Clam AV.

---

### Post by Mr. Svinlesha on 2007-08-21
Thanks, **ddrichardson**.

With "sudo service freshclam stop," Ubuntu returns, "sudo: service: command not found."  Then I removed /var/lib/clamav, as per your instructions.  Next, "sudo service freshclam start," same error message as the previous: "command not found."  Finally, "sudo freshclam" gets the message, "Can't change dir to /var/lib/clamav/", probably because I removed the directory (if I understand Ubuntu correctly).

Now what?

---

### Post by ddrichardson on 2007-08-21
Uninstall clam then reinstall. Actually I probably get flamed for this, but I prefer AVG Free for Linux. The whole updating thing just needs the user name added to the AVG group to allow permissions.

---

### Post by Mr. Svinlesha on 2007-08-21
I'm actually quite agnostic on the issue, would gladly switch to AVG, just as long as I have some virus protection.  I'm told I don't really need it, but just to be on the safe side....

How do I uninstall Clam?  "sudo uninstall clamav"?

I'd be interested in trying AVG myself.  Is it complicated to install?

Thanks again for the help and advice.

---

### Post by ddrichardson on 2007-08-21
Assuming it was installed from the repositories:```
sudo apt-get remove clamav
```Will do the trick.

AVG is [here]("http://free.grisoft.com/filedir/inst/avg75fld-r47-a1025.i386.deb") - and can be installed from Firefox with gdebi.

As for whether or not its needed, here's [my opinion]("http://uk.geocities.com/ddrichardson@btinternet.com/viruses.html") - I usually get slammed for it though.

---

### Post by Mr. Svinlesha on 2007-08-21
I've download AVG now, and it seems to work well.  It has a good rep too, so I'm happy.

Thanks again, **dd**.

---

### Post by ddrichardson on 2007-08-21
No worries.

---

### Post by technohive on 2007-08-21
Try to uninstall all your cookies and also see do some search since there might be some more files left in your pc. I have not used clam because am using AVG so I think you must see first if there are some files left in your pc.

---

### Post by ddrichardson on 2007-08-21
> **technohive said:**
> Try to uninstall all your cookies and also see do some search since there might be some more files left in your pc. I have not used clam because am using AVG so I think you must see first if there are some files left in your pc.

The only files likely to be left would be in /home/username/.clam. A sudo apt-get autoremove will clear and uninstall any dependancies no longer needed.

I'm not sure where you are going with cookies - they are only used by web browsers to store locally entered information rather than re-enter it every time a site is visited.

---

### Post by euler_fan on 2007-08-21
Since you seem happy with AVG free for Linux, you can consider this an FYI:

There is no point in installing many security apps from the central Ubuntu or even community repos. For example, ClamAV puts out an updated release every 2-4 months, which is FAR more frequently than the Ubuntu repos update it (since they are made static for each release). I want to say this is also true for rkhunter, chkrootkit, and several other "mainline" security apps. For that reason I usually advise that Clam and the rest are best installed from source using recently downloaded, verified files (hashes and/or gpg signatures).

This said, many other apps are usually fine even if a version or two out of date.

---

### Post by ddrichardson on 2007-08-21
> **euler_fan said:**
> Since you seem happy with AVG free for Linux, you can consider this an FYI:

There is no point in installing many security apps from the central Ubuntu or even community repos. For example, ClamAV puts out an updated release every 2-4 months, which is FAR more frequently than the Ubuntu repos update it (since they are made static for each release). I want to say this is also true for rkhunter, chkrootkit, and several other "mainline" security apps. For that reason I usually advise that Clam and the rest are best installed from source using recently downloaded, verified files (hashes and/or gpg signatures).

This said, many other apps are usually fine even if a version or two out of date.

Fair point, hence why AVG can be updated daily. Its the definitions that count here rather than the program code itself.

---

### Post by Mr. Svinlesha on 2007-08-21
Anyone who speaks English, feel free to hop in and translate at any time.

:)

---

### Post by euler_fan on 2007-08-21
> **ddrichardson said:**
> Fair point, hence why AVG can be updated daily. Its the definitions that count here rather than the program code itself.

It's not that Clam updates its signatures every 2-4 months, it's that it updates its scanning engine every 2-4 months. It's signatures change at least once per day. Moreover, newer signature types will only work with the more recent versions, therefore updating is necessary to get the benefit of all the latest signatures. That's part of that "Old version" error message the OP was getting earlier.

But since they are happy with AVG free, I thought I would merely point out for their general knowledge why installing security software from the repos must be done with care (if at all).

---

### Post by euler_fan on 2007-08-21
> **Mr. Svinlesha said:**
> Anyone who speaks English, feel free to hop in and translate at any time.

:)

Sorry about that:

The general idea is that Ubuntu is built on lots of software provided as packages. Well, when Ubuntu puts out a new release (like 7.04) on the day of release only the packages in the repositories (and hence available via Synaptic) are no longer allowed to be updated except to fix security and the occasional other critical bug.

Therefore, if a piece of software releases many updated versions (like ClamAV does) each year, the version Ubuntu distributes in the repositories is out of date forever. Thus the only way to get the "latest and greatest" is the install it from source.

I hope that helps some.

---

### Post by Kilz on 2007-08-21
> **Mr. Svinlesha said:**
> Anyone who speaks English, feel free to hop in and translate at any time.

:)

English - It doesn't matter if there are any definitions, or if it updates. The reason is that all the viruses it checks for are Windows viruses. There are a Whopping 0, thats right **[COLOR="Red"]0[/COLOR]** linux viruses.

---

### Post by euler_fan on 2007-08-21
> **Kilz said:**
> English - It doesn't matter if there are any definitions, or if it updates. The reason is that all the viruses it checks for are Windows viruses. There are a Whopping 0, thats right **[COLOR="Red"]0[/COLOR]** linux viruses.

Okay, true, it is scanning overwhelmingly for windows viruses. I like knowing I'm less likely to unwittingly pass something on in a forward from a friend or something like that.

I know, I know . . . windows users should take care of themselves, but I like being polite.

There are other signature file out there, like the [anti-phishing signatures]("http://www.sanesecurity.co.uk/clamav/usage.htm") from SaneSecurity.

And yeah, so maybe anyone who actually responds to a phishing scam on some cosmic level deserves what they get, but it demonstrates the power of the system to scan for whatever you do think is a threat as opposed to whatever someone else (like AVG) thinks is a threat.

But at least it [does well in tests]("http://www.darkreading.com/document.asp?doc_id=131246&WT.svl=news1_1").

---

### Post by ddrichardson on 2007-08-21
Correction - there are 0 linux viruses rated as serious known in the wild.

---

### Post by Kilz on 2007-08-21
> **euler_fan said:**
> 
I know, I know . . . windows users should take care of themselves, but I like being polite.
.

Exactly how many attachments do you send to people from someone else? Even so, how many Windows users even open attachments anymore? How many files do you get from someone else and then share? 
The only way to get a virus to pass is to download it in a file. Since most linux users dont download infected windows binaries the chance of getting one are small. That is if you dont forward infected attachments from others.

> **ddrichardson said:**
> Correction - there are 0 linux viruses rated as serious known in the wild.
Granted there are some proof of concept viruses. but they are not in the wild. They also require you to do something stupid. like run as root.

---

### Post by Mr. Svinlesha on 2007-08-22
So let me see if I can summarize this discussion so far:

1) I can't use ClamAV because the version I have on my computer is outdated.  It's outdated because it was downloaded from an Feisty Fawn repository that's “static”, and ClamAV has released a new version since Feisty came out.  For some reason, FF won't update new versions of ClamAV, and the latest virus definition files won't work with older versions of ClamAV.

2) If I want to use the latest version of ClamAV, I need to be careful and download it from an undisclosed source. 

3) It doesn't really matter all that much anyway, since neither ClamAV nor AVG scans for Linux viruses; at this point, I really only need an antivirus program as a courtesy to Windows users who might otherwise be infected should I send them viruses that work on their computers, but not mine.


**Kilz**:

> *Granted there are some proof of concept viruses. but they are not in the wild. They also require you to do something stupid. like run as root*.

I'm definitely stupid enough to do something like that.  Actually, I'm even too stupid – as I noted earlier in this thread, I've forgotten how to log in as root.  Maybe just as well.  

But I can easily imagine having originally set up my Linux OS so that I would log in as root at start up, and then using it that way for several months before figuring out I was doing something wrong.  The shear volume of material one has to digest as a new Linux user is, in all honesty, a bit daunting.

Anyway, one point of anti-virus protection, at least as I see it, is precisely that.  It's like “stupidity insurance.”  And it's necessary: I'm currently trying to help a workmate with her daughter's computer here on the side.  Daughter has been surfing and downloading like crazy with no virus protection.

Their computer is hosed, I tell you.  All because of user stupidity.

---

### Post by zero-9376 on 2007-08-22
One use I have for antivirus on Linux such as clamav is to scan windows computers over the network.

---

### Post by ddrichardson on 2007-08-22
> **Kilz said:**
> Exactly how many attachments do you send to people from someone else? Even so, how many Windows users even open attachments anymore? How many files do you get from someone else and then share? 
The only way to get a virus to pass is to download it in a file. Since most linux users dont download infected windows binaries the chance of getting one are small. That is if you dont forward infected attachments from others.


Granted there are some proof of concept viruses. but they are not in the wild. They also require you to do something stupid. like run as root.

And we go full circle again. Every time someone posts asking about virus protection the same thing happens. See my [home page link]("http://uk.geocities.com/ddrichardson@btinternet.com/viruses.html") for my 5p on Linux viruses.

If we continue to promote Ubuntu as an alternative for the average Joe we need to recognise that average Joe's friends run Windows so upstream protection is necessary unless we want a situation where his friends say "you gave my a virus" and Joe says "they told me that couldn't happen in Ubuntu" and goes back to Windows/Norton etc...

---

### Post by Mr. Svinlesha on 2007-08-22
Plus, I mean, it's at least theoretically possible to infect Linux with a virus or worm, isn't it?  So it's bound to happen sooner or later.

---

### Post by Mr. Svinlesha on 2007-09-22
I'd like to update my AVG database.  According to **ddrichardson**:> Uninstall clam then reinstall. Actually I probably get flamed for this, but I prefer AVG Free for Linux. The whole updating thing just needs the user name added to the AVG group to allow permissions.I assume by this he means I go System > Administration > Users and Groups.  And sure enough, I find avg there as a new group.

How do I add my user name to this group?

---

### Post by jean noel on 2007-12-12
> **gkey said:**
> 1st - to run virusscanner in graphical mode as root enter " sudo clamtk" in a shell.

for your other questions: have a look at this page on the wiki:
[https://help.ubuntu.com/community/ClamAV]("https://help.ubuntu.com/community/ClamAV")

I had the same problem. Whilst acknowledging that linux has fewer viruses than windows I wanted to install an antivirus. I had the same difficulty in updating clam.
With that command, everything worked fine.
Thanks old friend.
jean noel

---

### Post by AB34125 on 2008-01-16
> **zero-9376 said:**
> One use I have for antivirus on Linux such as clamav is to scan windows computers over the network.

I appear to have clamav working correctly on my machine.  But I can seem to scan my windows machine over the network.   Can you please help me or point me in the right direction.  

thank you.

---

