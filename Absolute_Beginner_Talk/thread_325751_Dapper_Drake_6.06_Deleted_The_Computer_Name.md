---
title: "Dapper Drake 6.06 Deleted The Computer Name"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Lost Traveler on 2006-12-26
While deleting entries in the Network section under Administration on the GNome desktop I deleted the computer name while deleting entries for a dialup that was not working.  Now, I am shut out of most functions including Network under the Administration button.  Any ideas on how to restore the computer name would be appreciated.

---

### Post by taurus on 2006-12-26
Boot into recovery mode from GRUB menu and edit both /etc/hosts & /etc/hostname.  They both need to have the same name...

```
nano -w /etc/hostname
nano -w /etc/hosts
```
Otherwise, boot from the LiveCD, mount your harddrive where / is located, and edit those two files on the harddrive!

---

### Post by Lost Traveler on 2006-12-26
Thanks, Taurus
   Now your talking to someone who is a bit shy about booting into Recovery mode, but I gave it a try.  The first try seemed successful entering the hostname, but I was not sure what I was looking at.  I ended up in a text editor with my new hostname at the top.  I did not know if I needed to enter any text or save it, but I sure had fun trying to get out of there.  I am still not sure how I did it.
   I saw no way to enter the second 'hosts/computername basically because Iwas stuck in the text editor and I did not know what to do.  So, I am still a little edgy about that route with my lack of knowledge.  
   On the other hand I think it would be nice if I could find a way to become more familiar with using the editor.  I understand that learning to use the Terminal is a real benefit.  Right now the only resources I have is the internet and a book titled; Ubuntu Linux For Non Geeks.  
   I remember not knowing where I was after I entered the first nano command or if I needed to do something before leaving that text editor.  How do I get the prompt ready for entering the second nano command?  And how do I get out of the text editor.  The 'ctrl' E did not work for exiting the editor......probably because I needed to do something else first.  Hey, it is a little baffling when you have not seen something like that before.
   Anyway, Sorry I was not able to get it right.
Lost Traveler

---

### Post by taurus on 2006-12-26
I assume you want to call your computer home.  Therefore, you should have the word **home** in /etc/hostname and your /etc/hosts would look something like this.

```
127.0.0.1       localhost     **home**
```

---

### Post by Lost Traveler on 2006-12-26
At the prompt I did this way:  nano -w /etc/hostname/home  enter

Now all I see is a blinking cursor in the editor text area.  What next?

---

### Post by taurus on 2006-12-26
> **Lost Traveler said:**
> At the prompt I did this way:  nano -w /etc/hostname/home  enter

Now all I see is a blinking cursor in the editor text area.  What next?
At the prompt (from recovery mode), type

```
nano -w /etc/hostname
```
Then, add the word **home** to it and don't hit the return key!  Just hold down <Ctrl> while pressing x and yes, and return key couple of time.  Then, do the same thing for the other file.

```
nano -w /etc/hosts
```

---

### Post by Lost Traveler on 2006-12-26
Another words, do not use the forward slash such as 'hostnamehome'  I will reboot this computer into Grub Ubuntu recovery mode and give it a try.
thx

---

### Post by Lost Traveler on 2006-12-26
No luck at all.  Can not get an exit without hitting the enter key and looking for another prompt at which I type 'exit' and hit enter key and recovery mode shuts down.  But still no name added.  At the bottom of the editor page just above the commands was this:
  [ New File ] highlighted, but I could not find a way to see if that 'New File' was necessary to make the new computer name work.  But I suspect it does need to create a new file for the computer name....is that possible?

---

### Post by taurus on 2006-12-26
> **Lost Traveler said:**
> Another words, do not use the forward slash such as 'hostnamehome'  I will reboot this computer into Grub Ubuntu recovery mode and give it a try.
thx
I have no idea what you are talking about forward slash and 'hostnamehome'!!!  You want to add the word **home** to /etc/hostname, just one single word in there...

And if it doesn't exit, nano will create one for you!

---

### Post by Lost Traveler on 2006-12-26
Ok.  I will try again.  At the prompt 'nano -w /etc/hostnamehome'   Is this the correct entry?  What I should not do is; 'nano -w /etc/hostname/home'   I will not do this.  Once the entry is made I will try to exit somehow.  The 'ctrl' E has not worked so far to exit.

---

### Post by taurus on 2006-12-26
At the prompt, type

```
nano -w **[COLOR="Red"]/etc/hostname[/COLOR]**
```
THEN, add **home** to the file.  To exit, hold down <Ctrl> while pressing x.  Then, yes, and hit the return key twice...

---

### Post by Lost Traveler on 2006-12-26
Taurus,  This last try worked for '/etc/hostname'.  I decided to use my name instead of 'home' and it appeared on the Log-In screen.  However, when entered: nano -w /etc/hosts  I saw a file with nine lines of data.  First line: 127.0.0.1 Local Host   Second line: 127.0.1.1 my name-desktop.  There is a space and then the following line:  The following lines are desirable for IPv6 Capable Host and below that was six more lines.  So, Where do I go from there?  I tried adding my name to the file, but it did nothing and I can not yet get into the Network under Administration.  So, I took my name out of the file.  Any ideas?

---

### Post by taurus on 2006-12-26
The second line in /etc/hosts is the one you need to change so it would have the same name as in /etc/hostname!

```
127.0.1.1 **my name-desktop**
```

---

### Post by Lost Traveler on 2006-12-26
Ok, I did not want to say my actual name here, but on that line 127.0.1.1 my name is on that line as  127.0.1.1 myactualname-desktop.  It may have been there all along for all I know, but I did not see my name appear on the log-on screen until I entered my name in the file '/etc/hostname'.   So, I am sure I got it in there correctly.  Is there a mystery here?

---

### Post by taurus on 2006-12-26
If this name, 127.0.1.1 **myactualname-desktop**, is the same as in /etc/hostname, then it should work!  See if you get any error message when you run these two commands?

```
ping -c 3 www.yahoo.com
gksudo nautilus
```

p.s.  You may have to reboot first though...

---

### Post by Lost Traveler on 2006-12-26
I have to log off of here and reboot into Linux from this machine.  It will be a few minutes.

---

### Post by Lost Traveler on 2006-12-26
Problem solved!  I noticed my log-in screen displayed 'myname' and not 'myname-desktop' which told me that the file was not the same as my 'myname' entered into the first file.  So, I changed it and everything works just as you said it should if both files had the same name.
   I must say this has been an experience.  Twenty some years ago I took a school course in DOS and I need to unlearn what little I know of it.  Linux is different. 
   This problem began with my attempts to get my pci win modem to work.   It will dial out, but beyond the dialing it does not work.  I probably need a driver.  Anyway, many thanks for staying with me and helping me out.  I learned that I MUST get on better terms with the terminal and file editing.  I am sure it will not be my last screw up. Many Many Thanks.
Lost Traveler.

---

### Post by taurus on 2006-12-26
A lot of people somehow decided to change the name of their computer to something else after they installed it, not realizing that they had to change both /etc/hostname & /etc/hosts.  Then, they would find out that they couldn't run sudo anymore and their network was dead as well...

So, always be careful when you decide to make any change to your system's files.  

However, glad to hear that you are back to business again.

---

### Post by maniac_X on 2006-12-26
> **Lost Traveler said:**
> 
   This problem began with my attempts to get my pci win modem to work.   It will dial out, but beyond the dialing it does not work.  I probably need a driver. 

With regard to your winmodem situation.....winmodems are the bane of linux. Most drivers for them are not opensource(and require thier purchase) and/or written for Winbloze. Add to that the selection of non-winmodems is getting very sparse these days. You will find in these forums a number of discussions regarding the winmodem user's problems. Some have success after a time, after much fiddling and compiling, and some don't. The concensus seems to be that an external serial modem is probably the easier solution.
I myself have 2 computers currently at my location both with internal modems. One of them is recognized out of the box when installing both Breezy and Dapper versions of Ubuntu. The other(which is my primary machine) sadly does not work.  I have already ordered a cheap external serial modem. Pending positive results, I will pass on to you where I bought it.

---

### Post by Lost Traveler on 2006-12-26
If someone knows how to show this thread as resolved, please do so.  I have poked around this site for half hour trying to find how to show this thread as resolved.  I did not have any luck finding 'Advanced Options' that I read would offer the Resolved option.
Thanks

---

