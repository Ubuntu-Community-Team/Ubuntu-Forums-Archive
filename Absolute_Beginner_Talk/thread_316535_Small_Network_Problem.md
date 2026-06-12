---
title: "Small Network Problem"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-10
I've seen references to this problem in the last couple of weeks but no solution.  New install of Edgy, dual boot with Win XP.  In Nautilus, click on Network Servers > Windows Network.  In the next window the network name (MSHome--very original) is shown with a generic icon that looks like it's for a text file.  Clicking on it gives an error:  **"Couldn't display "smb:///mshome".**  The location is not a folder."  By clicking on the icon a few more times, or hitting Reload, the icon will change to the server icon and clicking on it gives me the next window.  Here there's the same problem with each of the computer names on the network.  Once I get past that the network file browsing works normally.

Anyone know how to fix this?  I'd appreciate the help.

Thanks,
Buck

---

### Post by Atomic Dog on 2006-12-11
I have a similar symptom.  I haven't needed it badly enough to search the forum for the solution.  Eventually I will need to figure out why this quirk exists.

---

### Post by lucky_chouhan on 2006-12-11
1. Check Workgroup 
2. Check Xp Sharing Any Folder Or Drive.
3. Open Terminal And Ping The Ip Address.
4. Type The Ip Address Rather Then Client Name.

---

### Post by victorbrca on 2006-12-11
IMHO, if you haven't checked, try these:

- SMB server is installed
- System => Administration => Shared Folders (add one) => Properties => General Windows Sharing Settings => Change Domain/Workgroup name if required


Vic.

---

### Post by Buck2348 on 2006-12-11
> **lucky_chouhan said:**
> 1. Check Workgroup 
2. Check Xp Sharing Any Folder Or Drive.
3. Open Terminal And Ping The Ip Address.
4. Type The Ip Address Rather Then Client Name.

Not sure of the meaning of (1.)  The Workgroup name is correct everywhere I've seen it.  (2.)  Sharing is set up in the Windows systems--I can eventually reach the shares--just takes several clicks.  (3.)  I can ping the other systems.  (4.)  Works, but is a pain to do while working with network files.


> **victorbrca said:**
> IMHO, if you haven't checked, try these:

- SMB server is installed
- System => Administration => Shared Folders (add one) => Properties => General Windows Sharing Settings => Change Domain/Workgroup name if required

- Samba is installed
- By "Change Domain/Workgroup name if required" I assume you mean change it if it's incorrect.  But it is correct.

Thanks all for your replies.  I need a little more help with this.

Buck

---

### Post by Iowan on 2006-12-11
Try using Places>Connect to Server.
It seems to work better for me. You might also check your user privileges (System>Administration>Users and Groups>[username]>Properties>User Privileges) to see if "Enable access to external storage devices automatically" is checked.

---

### Post by The Mekon on 2006-12-12
This is a problem on my Ubuntu Edgy machine.  By clicking reload I eventually get all four of our computers to show up properly.

The interesting thing is that Kubuntu Edgy machine does not have any problem finding all four machines immediately.

It looks like a bug in Gnome.

Brian

---

### Post by Buck2348 on 2006-12-12
Yes.  But I never had the problem with Ubuntu Dapper.

Buck

---

### Post by Atomic Dog on 2006-12-13
> **Iowan said:**
> Try using Places>Connect to Server.
It seems to work better for me. You might also check your user privileges (System>Administration>Users and Groups>[username]>Properties>User Privileges) to see if "Enable access to external storage devices automatically" is checked.

This does work without fail.  I have to do the same thing when our snap server wiggs out and won't authenticate AD users.  The problem is most people don't even realize there are ip addresses behind the machine name in a network, it can get confusing to remember the ip - especially when there are a couple hundred machines.  The convenience of browsing the network or workgroup is unarguable.

There is a bug/quirk in nautilus when it comes to browsing a network.  I just hope it gets fixed.

---

### Post by victorbrca on 2006-12-19
It's a bug!!!


[Launch Pad]("https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277")


Vic.

---

### Post by Buck2348 on 2006-12-20
> **victorbrca said:**
> It's a bug!!!

Aha!  I thought as much.  I went to launchpad and though they mentioned a patch I couldn't find one there.  I tried downloading and installing an "Extra" package for gnome-vfs2.17, but of course it wouldn't install.  I downloaded the main 2.17 package but since it was targeted for feisty I thought better of trying to install it.  I don't really understand why at the launchpad they talk about a workable patch for this bug but they don't offer to let one have it.

As has been mentioned in other posts, if you don't want to click "reload" a few times to access the shares, using "Connect to Server" once for each machine on the network will put an icon for the machine on the desktop and in the Network Servers Window.  Mounting the shares as a file system is even better--works faster.  I realize that either of these would be a chore on a large network.

Thanks, victorbrca, for your post.

Buck

---

### Post by victorbrca on 2006-12-20
> **Buck2348 said:**
> Aha!  I thought as much.  I went to launchpad and though they mentioned a patch I couldn't find one there.  I tried downloading and installing an "Extra" package for gnome-vfs2.17, but of course it wouldn't install.  I downloaded the main 2.17 package but since it was targeted for feisty I thought better of trying to install it.  I don't really understand why at the launchpad they talk about a workable patch for this bug but they don't offer to let one have it.

As has been mentioned in other posts, if you don't want to click "reload" a few times to access the shares, using "Connect to Server" once for each machine on the network will put an icon for the machine on the desktop and in the Network Servers Window.  Mounting the shares as a file system is even better--works faster.  I realize that either of these would be a chore on a large network.

Thanks, victorbrca, for your post.

Buck


No problem!!!!!!!

I solved mine trough a mount as well!!!! It even allows me to execute files over the net, which due to the bug I couldn't !!!


Vic.

---

