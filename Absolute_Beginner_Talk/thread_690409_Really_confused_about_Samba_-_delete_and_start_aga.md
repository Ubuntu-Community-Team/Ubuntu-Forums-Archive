---
title: "Really confused about Samba - delete and start again?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Twizzle on 2008-02-07
I am now very confused in relation to file sharing. I originally had three computers networked:

Office (XP) - Server (Ubuntu) - MediaSystem (XP)

I managed to configure Samba to let both Office and MediaSystem read and write to the server.

I then converted Office (XP) to Office (Ubuntu) :), and again could read and write to the server with both machines.

I have now decided that a Server is overkill and in an effort to save money and the environment have moved all my HDD's to the MediaSystem so I am left with:

Office (Ubuntu) - MediaSystem (XP)

I did not change any settings on my Office PC and could see the MediaSystem but not the drives inside (I had set to share and disabled the firewall etc etc). Both are members of WORKGROUP and both have the same username and password set.

I then did a bit of reading and *think* I might have to reconfigure Samba. Is this right? I only want to read / write from the XP machine. I am not bothered about the other way.

I did blindly follow a few guides and have managed to loose the Windows Workgroup from Places > Network!

I guess my question is, do I really need Samba for this? Can I uninstall it and start again?

---

### Post by emarkd on 2008-02-07
If I understand correctly, you can to set up your Ubuntu box as a Samba server and connect to a shared resource there using the XP box.  [Here's]("https://help.ubuntu.com/community/SettingUpSamba") a good guide for that.

---

### Post by bodhi.zazen on 2008-02-07
And this link as well :

[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by drubin on 2008-02-07
Try mythbunu as a media server!! 

it does all that.. very easy to configure

---

### Post by Twizzle on 2008-02-07
Thankyou for the advice so far.

Here is the really odd thing now...

I have Virtualbox running XP and have manged to connect to the shared drive on that from:

Places > Network > Windows Network > Workgroup > mediaportal

That VirtualPC is not called 'mediaportal' so how come it comes up like that!?

I am giving up for tonight and will try again tomorrow.

Rubinboy - I just might try that! But I don't like to be beat, even by Windows..

---

### Post by drubin on 2008-02-08
Converting to linux is letting windows beat you,

But rather you beating windows....

---

### Post by BLTicklemonster on 2008-02-08
Look at the link in my sig.

---

### Post by drubin on 2008-02-08
why is that your sig???

---

### Post by BLTicklemonster on 2008-02-08
lol so next time I reinstall ubuntu I can find it.

:)

---

### Post by drubin on 2008-02-08
Email/  text files??

but on a whole that is one of the funniest reason i have ever heard, but clever..

---

### Post by sirzepp on 2008-02-08
I don't know if this helps, because I am completely new as well...but I've had luck with getting samba to work by playing with the permissions on my Linux machine.

Samba seems finicky, so I only use the client/configuration helpers built into Ubuntu.  I tried some other managers but they just screwed up my smb.conf file.

The permissions issue is one that has bothered me before(especially when adding a new share).  I don't know what would cause problems with your Ubuntu machine not seeing the windows machine...I've not really had problems on that side of things.

---

### Post by Twizzle on 2008-02-08
Well I have given in and binned Windows (intrepid cheers....)

I must say that Mythbuntu installed very quickly and so far seems a very very good alternative to XP and MediaPortal.

I just need to figure out how to set up VNC and share my drives - should be easier than all that Windows rubbish - I managed to really mess up XP before I quit on it!

Thankyou for everyones help :)

---

### Post by emarkd on 2008-02-08
Sharing the drives is very easy.  NFS is there if you want to set it up, samba too.  sshfs is VERY easy to get going because there is no setup, but if your computers are older it's an additional layer of calculations to make.

---

### Post by Twizzle on 2008-02-08
Well VNC works just fine but I still can't share the drives!

I have the two large HDD drives which I have now set up in Mythbuntu to share (they are still ntfs if that makes any difference). When I go to my Ubuntu box and Places > Network, the only thing I get is a Windows Network.

I am now thinking that all my playing around to get an XP share to work has messed the configuration for Samba on my Ubuntu box. Can I just uninstall and then reinstall?

And emarkd:

> Sharing the drives is very easy.

I am sure it is very easy to you, but I am a real Linux newbie so get confused with what appear to me to be a vast number of options and choices. (I have been using Windows and DOS for the last 16 years or so and Linux for about two weeks.....)

---

