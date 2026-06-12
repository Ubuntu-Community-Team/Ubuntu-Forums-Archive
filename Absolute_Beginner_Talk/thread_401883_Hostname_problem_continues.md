---
title: "Hostname problem continues"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by groeswenphil on 2007-04-05
[SIZE="3"][FONT="Arial"][COLOR="Navy"]First, thanks to everybody that has tried helping me with this issue. Sadly it's still not fixed.

I first noticed that something was wrong when Synaptic wouldn't load.
As time passed, I noticed that a few other things weren't working correctly.....automatic updates, networking and a few other things.

My new best friend HymnToLife figured that I'd somehow messed up my hostname.
When I do this,

philip@Ubuntu:~$ cat /etc/hostname

I get this.


Ubuntu
philip@Ubuntu:~$

When I do this:-




philip@Ubuntu:~$ cat /etc/hosts

I get this:-

127.0.0.1 localhost Ubuntu
127.0.1.1 ubuntu


# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
philip@Ubuntu:~$
philip@Ubuntu:~$

Then, she advised me to do this in recovery mode.

nano /etc/hosts

edit the 'ubuntu' to 'Ubuntu'.

Which I did.............but nothing changed.
I also tried every possible permutation of u and capital U


Sadly, nothing changes.

I've a feeling that all this came about when I was messing in the Ethernate interface, trying to get my network running correctly. Now I can't even get Networking to run at all.

I'm wondering, is there a System Restore function like in Windows, or would I be better off simply re-installing Ubuntu.

Thanks in advance,
Phil[/COLOR][/FONT][/SIZE]

---

### Post by Zimmer on 2007-04-05
127.0.0.1	localhost.localdomain	localhost	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

is , I believe , what your 'vanilla' HOSTS file should look like.

Then have a look at Networking to check the hostname matches there (now it is lowercase) .

The error may have occured from the entry 127.0.1.1  

127.0.0.1 is the internal address for your computer  ie. The Host...

---

### Post by groeswenphil on 2007-04-05
How would I change it?

And let me get this right............I change ubuntu to Ubuntu?

Thanks,
Phil

127.0.0.1 localhost.localdomain localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

is , I believe , what your 'vanilla' HOSTS file should look like.

Then have a look at Networking to check the hostname matches there (now it is lowercase) .

The error may have occured from the entry 127.0.1.1

127.0.0.1 is the internal address for your computer ie. The Host...

---

### Post by groeswenphil on 2007-04-05
Hi,
I changed ubuntu to Ubunto in safe mode:- nano /etc/hosts

Then I clicked ctrl x
Then it says something like 'save to file        etc/hosts

I'm not sure what to do at this point, also what is the command to get the computer to re-boot?

Phil

---

### Post by Zimmer on 2007-04-05
> **groeswenphil said:**
> Hi,
I changed ubuntu to Ubunto in safe mode:- nano /etc/hosts

Then I clicked ctrl x
Then it says something like 'save to file        etc/hosts

I'm not sure what to do at this point, also what is the command to get the computer to re-boot?

Phil

The name you have saved in the hostname file  and the name you specify in the  hosts  file should match .

Use nano to view/edit  the files.

As a previous poster said in your earlier thread,  Ctrl + o  (the letter o)  'saves' the changes.
Ctrl + x will exit nano.

shutdown -r now

will reboot the machine.

---

### Post by groeswenphil on 2007-04-05
Well, I've learned how to shut down nicely when I'm in recovery mode.  :) 

Now, this is what I see on the screen after nano /etc/hosts

127.0.0.1 localhost localdomain localhost Ubuntu
127.0.1.1 Ubuntu


But still, automatic updates, Synaptic, Networking, automatix...........none of them work.

Tried this in Terminal:-

philip@Ubuntu:~$ cat /etc/hostname
Ubuntu
philip@Ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost localdomain localhost Ubuntu
127.0.1.1 Ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
philip@Ubuntu:~$


This is so frustrating.
I've had this computer for a month now........and until yesterday I had this annoying problem on the Windows partition........but Ubuntu was 100% reliable. Then yesterday I fixed the Windows problem , now Ubuntu has gone pear shaped.

You don't live near Cardiff do you?
All the best,
Phil

---

### Post by Zimmer on 2007-04-05
remove the line

127.0.1.1 Ubuntu

or put a # sign at the beginning of it  to comment it out. I think that is part of your problem.

and, no, I do not live near Cardiff....

---

### Post by Zimmer on 2007-04-05
..and localhost.localdomain      notice that part is joined by a   .   (full stop)  


127.0.0.1 localhost.localdomain localhost Ubuntu

I have no doubt that your skills with nano will soon be second to none... :)

(I had to go and re read my hosts file several times before confirming there was a full stop there....)

---

### Post by groeswenphil on 2007-04-05
Thanks...........but it still doesn't work............and my scanner has stopped working too. Ubuntu fails to find it although it's sat right beside the computer.

Anyway..........I put the full stop in, but that doesn't appear to have fixed it.

I took out the line 127.0.1.1 rather than comment it out.
You won't believe it, but when I built this computer I bought a great cordless keyboard from Amazon failing to realise that it wasn't a standard UK keyboard.

I can't find the hash key:confused: 

Now, I went to my computer file, found the etc folder and looked for a host file.
There wasn't one.

I guess that might be an issue?

Had you lived near Cardiff, you would have been dining well this evening.

Many thanks,
Phil

---

### Post by Zimmer on 2007-04-05
> **groeswenphil said:**
> Thanks...........but it still doesn't work............and my scanner has stopped working too. Ubuntu fails to find it although it's sat right beside the computer.

Anyway..........I put the full stop in, but that doesn't appear to have fixed it.

I took out the line 127.0.1.1 rather than comment it out.
You won't believe it, but when I built this computer I bought a great cordless keyboard from Amazon failing to realise that it wasn't a standard UK keyboard.

I can't find the hash key:confused: 

Now, I went to my computer file, found the etc folder and looked for a host file.
There wasn't one.

I guess that might be an issue?

Had you lived near Cardiff, you would have been dining well this evening.

Many thanks,
Phil

The file in /etc is  hosts  (with an s)

should have this in it
> 
 127.0.0.1 localhost.localdomain localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

/etc/hostname

> ubuntu
then your computer will now be called  'ubuntu'   

as for the scanner, if it worked before you may have a dodgy connection/plug not in properly. Had that happen myself, spent hours looking through logs, terminal commands, swearing.. etc etc. before trying the obvious...

---

### Post by groeswenphil on 2007-04-05
Let me get this right.
I type this into a text editor

127.0.0.1 localhost.localdomain localhost ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

and save it as a file.............but I need a filetype don't I?

Secondly..........and you might be able to hear me screaming...........when I go into etc and try to create a folder called hosts, the computer tells me that I don't have permission to do that.

I tried creating a hosts folder on the desktop and dragging it over.........didn't work.

Maybe I'd be better off uninstalling Ubuntu and starting over?

All the best,
Phil

going out for half an hour to collect wife and relax my brain in the traffic.

---

### Post by Zimmer on 2007-04-05
You have it right, but as you read on your other thread you must do this in Recovery Mode as the Root user.  Root has the permission to alter system files.

In other circumstances you would be able to edit such files using the sudo command from the terminal,
eg.  sudo nano /etc/hosts

but because the hosts file is missing/corrupt sudo is confused too...

As for no file extensions, that is not a problem. If you do a search on a Windows machine you will find a hosts file, again with no extension, and it works in the same way to give your computer a name and address.

If you want a chat about it then let me know and I will PM you my phone number. Be aware that Spurs kick off at 7:45...
:)

---

### Post by groeswenphil on 2007-04-05
I would indeed be eternally greatful and not keep you away from the box..............despite it being a silly game where grown men kick a ball around a field kissing each other.
On the other hand..........Rugby Union Football. Now there's a game.

Phil

---

### Post by Zimmer on 2007-04-05
check your private messages

---

