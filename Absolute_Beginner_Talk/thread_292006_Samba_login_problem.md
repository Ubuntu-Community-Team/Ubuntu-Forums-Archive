---
title: "Samba login problem"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by dudeeh on 2006-11-03
I have a bunch of shared folders (through samba) and they are working rather fine, except for one thing: when i log in on my computer (which happens to have the same username as one of the samba users), i can access a share without problems, but when i access it from someone elses computer, samba dutifully pops a login screen, but i can NOT enter a username. It is deactivated and has a standard "Guest" as username. 

How can i set it so everyone gets a popup where they enter a username as well as a password?

---

### Post by BLTicklemonster on 2007-11-11
October of 06, and still no answer. 






See why I rail on so much about how Ubuntu needs to pioneer "easy networking" in Linux?

---

### Post by Dr Small on 2007-11-11
October of 2006. This fellow may have been using Dapper or some older version.
Things are pretty easy in newer version, I think.

Dr Small

---

### Post by BLTicklemonster on 2007-11-11
I beg to differ:
[http://ubuntuforums.org/showthread.php?t=610090](http://ubuntuforums.org/showthread.php?t=610090)
Why do you think I was looking at samba login threads in the first place?

---

### Post by ant2ne on 2007-11-11
I'm no samba expert but I bet your problem is in one of these 5 steps....

**First thing**
be sure you have samba, samba-common, and smbfs installed. 

**next thing, firewall**
you need to be sure that your Linux firewall will permit smb connections. If not you are wasting your time. If you don't have a firewall installed on the linux share, guess what? By default access is denied. Install a firewall to open access. I suggest firestarter.

**3rd, you need a Guest Linux user**
You can't log into a computer with the guest name, unless you have a guest user name on that computer. It is the same with Windows but it has a guest user by default. Linux doesn't have a guest user by default.

you need a user named guest
```
adduser guest
```

now you need a guest samba user and password
log off and back on with guest and set the guest password
```
sudo smbpasswd -a guest
```

```
cat /etc/samba/passwd
``` be sure there is an X after the [U  for the guest account. This keeps the password from eXpiring. If no X, then edit the /etc/samba/passwd file and put in the X. Remember to delete a blank space to fill that space with the X as only 8 chars can be inside -> [ ]


Sample smb.Conf
[Global]
workgroup = YOURGROUP
netbios name = HOSTSNAME
guest account = guest  #This directs the log on of guest to the guest account you created

[OpenShare]
path = /yourpath
create mode = 0777
directory mode = 0777
writable = yes
guest ok = yes  #This permits the guest log on

**4 Windows drive mapping**
Also, if mapping a network drive in Windows, there is a hyperlink for  "Connect using a different user name". Click that and enter a valid user name and password for the Linux share and you should connect.  This is a good way to test the share with a known good name and password. Do not check the box to remember, unless it will be this users default (borrowed) name and password. 

**5, Permissions**
Permissions on a share are still important. If you do not have user access for guest then guest can't access the share. You may need to add an everyone group and then. Double check the path to share! I've trashed my system with a chown command.
```
sudo chown guest:everyone -R /PathToShare
```
Then
```
sudo chmod 777 -R /PathToShare
```
[B]
I suggest you google all of the terms above and become familiar with them.[/B]

Honestly, samba shares aren't much more difficult that XP-Pro's sharing. Granted Windows Home supports simple file sharing, and it is simple, but not very secure.

---

### Post by BLTicklemonster on 2007-11-12
This part confuses me:

be sure there is an X after the [U for the guest account. This keeps the password from eXpiring. If no X, then edit the /etc/samba/passwd file and put in the X. Remember to delete a blank space to fill that space with the X as only 8 chars can be inside -> [ ]

Seeing as I'm not sitting in front of the machine at present, and it may well be a while before I am, I'm trying to get as much figured out before I go back home. 

Are you saying that it should show

[UX for the guest account? That's what it looks like you are saying, and I want to be sure I understand.

thanks.

---

### Post by ant2ne on 2007-11-12
> **BLTicklemonster said:**
>  [UX for the guest account? That's what it looks like you are saying, and I want to be sure I understand.thanks.Yes that is what I'm saying. It should look like```
 [UX        ]
```Be sure to delete one empty space within the brackets as it is supposed to have a set number of characters within the brackets. Honestly I don't know if it matters, it is just what I read (somewhere) so I just do it that way.

---

### Post by BLTicklemonster on 2007-11-12
now you need a guest samba user and password
log off and back on with guest and set the guest password


what? Log off as in "log off" then log in.. how? I'd have to already set a password to log in to desktop, right? Log off samba? I didn't know I was logged in. How?

... and there's no gui for all of this...

sheesh.

I mean, come on, I don't care how secure it can be, there ought to be a stinkin' gui for it so I just fill in some lines and it's done.

---

### Post by BLTicklemonster on 2007-11-13
No, wait, I can see where this is headed, just never mind. I can live without this mickey mouse networking. 

Thanks anyway.

AS if this isn't enough of a headache, I'm trying to get one of the printers that is supported according to the ubuntu page that shows what printers are supported to work. Guess what? Yeah, the same numbskull who wrote the networking for linux wrote the printer stuff, too. Nope, the HP Deskjet720C does not print, no matter what.

Whee.

---

### Post by ant2ne on 2007-11-13
log off. 
The red button that you use to shut down the computer. It also has a log off function. This logs of a user so that another user can log in. Log off with your primary user, and then back in with the guest account you just created.  I don't think you can set the password for a user, from a different users account. Thus logging in and out. Windows also supports logging in and out. When a newly created windows user logs in for the first time "magical things" happen. I'm not sure, but I bet linux is the same in that regards.

---

### Post by BLTicklemonster on 2007-11-17
> **ant2ne said:**
> Yes that is what I'm saying. It should look like```
 [UX        ]
```Be sure to delete one empty space within the brackets as it is supposed to have a set number of characters within the brackets. Honestly I don't know if it matters, it is just what I read (somewhere) so I just do it that way.

Where?

---

### Post by jivabill on 2007-11-21
Been reading this thread with interest.  I have to say that I TOTALLY agree with Ticklemonster.  Ubuntu docs on networking are woefully inadequate.  And one certainly should not have to resort to command line magic to make it work either.  That was the dark ages. 

I been in computers since 1958.  Worked in Mainframes for 25 years: programmer, Systems Analyst for major corporations and government agencies, Data Processing Manager.  I can tell you that in that time I went thru a LOT of blackmagic.  But we are supposed to be in the enlightened age of GUI's and good docs.  Supposed to be.  NOT.

 Software must be user friendly.  A lot of Ubuntu docs are quite good.  But the area of networking is a big failure so far.

I am stuck myself.  I have a Win98SE machine that I want to network with my Ubuntu machine.  I can see and manipulate files and the printer from Ubuntu to Win.  Not the other way, no how no way.  I have spent HOURS on this with no success.  I followed the Youtube PC Mechanics film, sounded good.  BUT when I get down to the part where I want to access a shared file on the Ubuntu box from the Win box I can't.

The system askes me for a password at the Win machine, tried to map a network drive.  NO password works, not the one I set up in Samba, not the pass for admin, blank password, nothing.  No remedy in sight.

I guess, from my reading the remedy is just to wait and wait until one of the Ubuntu Geeks decides to do something about docs.

Like ticklemonster said, heck of a way to run a railroad.
My two cents
Bill

---

### Post by BLTicklemonster on 2007-11-21
How cool. My name's Bill, and I was born in 58. 

:)

Let's hope someone figures this out.

---

