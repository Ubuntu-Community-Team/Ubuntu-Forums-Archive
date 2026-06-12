---
title: "Home Network with Windows"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by JWWWONKO on 2008-04-02
I am a NEWBIE and I think I am in way over my head, any help is appreciated.
I started with a home network setup in Windows XP.  Main computer 'A' and  2 others 'B', and 'C'.
I installed Ubuntu on computer 'B'.  I read thru some of the forums and installed Samba.

Now computer 'B' can see and access the files on computer 'C' but it can't seem to connect to computer 'A'.  When I go to Places\Network I can see my windows home network.  When I click computer 'C', I get all of the appropriate folders.  When I click computer 'A', I get an error "The folder contents cannot be displayed'.  

It seems like this would be a permissions issue, I have not changed anything on computer 'C' to make it accessible.  SO why can't I get to computer 'A'?

be gentle with me, you may be dealing with a borderline idiot. :lolflag:

---

### Post by saj0577 on 2008-04-02
I had this problem specific to certain folders not computers, just double check the settings and even disable then reenable them on computer A. I cant remember how i fixed my problem sorry, all i know is i fiddled with permissions.

Saj

---

### Post by Iowan on 2008-04-02
Does "A" have the Firewall running?

---

### Post by JWWWONKO on 2008-04-02
I read somewhere about the firewall, so I made sure that was turned off.  I also made sure all of the folders I want to access on machine 'A' are shared.  But I still get the error when trying to get to machine 'A', no problems with machine 'C'.  (In windows, I can access all of the machines, no troubles)

---

### Post by JWWWONKO on 2008-04-09
Well, I guess I am on my own  :confused:

It was great when 2 different people responded so quickly, then nothing.....

I saved a document today on computer 'C' and then I could access it from computer 'A', just seems a little roundabout way of doing things.

---

### Post by FiremothPilot on 2008-04-09
I would highly recommend ensuring that all of your machines running Windows XP are all in the same workgroup.

In the 'System Properties' window (Windows key + Pause/Break or right-click 'My Computer' and select 'Properties...') select the 'Computer Name' tab. Make sure all WinXP machines say the same thing under the 'Workgroup' field. By default, Windows workgroups are called 'WORKGROUP'. It might be easiest just to use this name.

If any changes are made to workgroup names, a system restart will be required.

Sorry is this seems overly-simplified. You said you were pretty new to everything.

---

### Post by JWWWONKO on 2008-04-10
I prefer overly simple, thanks!
I checked them out and all 3 machines have 'MSHOME' as the workgroup.

---

### Post by herbster on 2008-04-10
> **JWWWONKO said:**
> Well, I guess I am on my own  :confused:

It was great when 2 different people responded so quickly, then nothing....

1) Be patient, this is a free forum, you get what you pay for and 2) That unappealing attitude isn't going to win over a flock of help from most folk.

As to your problem, I'm a bit confused: Which OS is on each? From mentioning Places > Network I'm guessing one is XP and at least one is Ubuntu, can you clarify which is which? This should be a pretty simple thing to solve.

---

### Post by Tteddo on 2008-04-10
On computer A do you have anything shared? Folders' printers, etc...if not, you will get the exact error you are getting.
On Computer C can you see all 3 computers in My Network Places? (Click View Workgroup Computers on the left to see them if you have to).
What about Computer B, can you see the other 2 in Network Servers?
Just a silly question, but are you sure they are all in the same network space (i.e 192.168.1.X)?

---

### Post by JWWWONKO on 2008-04-10
I apologize if I offended anybody.

The home network was originally all Windows XP, the printer is attached to computer 'A' and its shared with the other computers.  

I think Ubuntu is an awesome way to go, so I am trying it out by installing it on computer 'B'
'B' is the only computer with Ubuntu.  From 'B', I go to PLaces\Network and I can see 'Windows Network' icon.  If I click that, I can see computer 'A' and computer 'C'.  I can open folders on 'C', but I get the error when I try to open folders on 'A'.  Both drives on 'A' are shared.

'A' is my main computer, and it has all of the data that I want to be able to get to.

When I open up My Network Places on computer 'C', I don't see computer 'B'.  If I try to map a network drive from 'C', I can see UBUNTU, but I can't make the connection.
I can save and move files from 'B' into the folders on computer 'C'
I dont know how to tell if they are all in the same network space.

thank in advance for any insight you can offer.

---

### Post by david_kt on 2008-04-11
Could you follow below instruction and report back what happen:

[http://ubuntuforums.org/showthread.php?t=103328&highlight=Newbie+folder+Windows+LAN](http://ubuntuforums.org/showthread.php?t=103328&highlight=Newbie+folder+Windows+LAN)

DK

---

### Post by herbster on 2008-04-11
And you are sure that Ubuntu is in the same workgroup? I know you posted above that they are, it's just that this is quite often the issue.

Or it could be a permissions issue. Are you trying to get into the drive itself from B->A, or more specific folders like the Desktop or Documents and Settings on A? You need to set those folders to shared as well, not just the drive.

Now if that is not resolving it, the best way IMO is to very simply mount the drives using cifs so they're mounted on each boot-up, just the same as any regular drive on your machine. You edit your filesystem table, but first we make a directory where your computer A will be mounted, for example:

```
sudo mkdir /media/xp-a
```

Of course, change "xp-a" to whatever you want, like "myxpbox" or what have you. Now we edit the filesystem table:

```
sudo gedit /etc/fstab
```

Add these lines, **after**, obviously, replacing the capitalized terms I have below with your own:

```
//192.168.X.X/PATH/TO/XP /media/xp-a cifs user=USERNAME,pass=PASSWORD
```

Replace with your ip, the path to your XP shared folder, and your user/pass on your XP machine (if you have a user/pass, otherwise exclude that portion from the above line). When done this, run

```
sudo mount -a
```

If you get no output, just another prompt, then it worked. Go to your file browser and go to /media, find the directory you made and open it, see what happens.

---

