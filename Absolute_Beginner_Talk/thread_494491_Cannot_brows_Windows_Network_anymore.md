---
title: "Cannot brows Windows Network anymore"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Ron F. on 2007-07-06
I have been a Windows user since ... since the beginning. I am a new Ubuntu user as of last week. The transition is proving difficult for me. I guess the new generation kids will be Linux users, and my generation will just have to die off before we stop using Windows. I feel like I might be that balding PC guy on the  Apple ads.

I installed 7.04 and got it running. It has worked for several days, and I have made /etc/fstab entries for shares that are hosted on my company's Windows machines. I have been able to browse the Windows Network through the Nautilius File Browser without any trouble ... until I did a reboot today - now none of that works anymore. When I try to browse the Network, I get the error:

Couldn't get main dbus connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Starting Nautilus as root had given me:

running "mount -a" gives me:
Nautilus-Share-Message: ------------------------------------------
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: usershares are currently disabled

Is that relavent? 

Running "mount -a" by hand gave me:

7693: Connection to ntws failed
SMB connection failed
7694: Connection to ntws failed
SMB connection failed

A typical /etc/fstab entry looks like:
//ntws/Root /media/Rdrive smbfs username=***,password=***,dmask=777,fmask=777 0 0

I am exhasperated - this was working out of the box. Now, I cannot browse the Windows Network. A quick check on a Windows XP machine indicates the WINS server is running just fine and my name and password work fine too. I also have access to the network and the internet - so the problem is in my Ubuntu machine.

I know there are a LOT of pages on the web about mount, samba, smbmount, smbfs, etc., that is part of my problem - complete information overload. I am annoyed by this. I don't know what is useful to me and what is not.

How do I get access again to the Windows-hosted shares, or browse the Windows Network in the Nautilus File Browser?

Thank you,
Ron

---

### Post by p_quarles on 2007-07-07
I'm just getting my feet wet with Samba myself, so I'm not sure how much I can help, but I will try.

First, I'd try reconnecting to the server using the Places >> Connect to server option. Then choose the "Windows share" option, and type in your user name and the server location (the rest you can leave blank). It's preferable to use the numeric IP address rather than the domain/computer name. 

Second, failing that, the fact that you got a dbus error message suggests it might have something to do with a kernel error that's been popping up recently. Try running (from the terminal): ```
sudo /etc/init.d/dbus restart
```
and then browse for the network.

If those don't work, I can only hope someone else here has a suggestion.

---

### Post by Ron F. on 2007-07-07
p_quarles,

Thank you very much! I will try your sugguestion as soon as I get into work on Monday, it is my desktop at work:)

-Ron

---

