---
title: "samba file sharing"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by madeupname on 2007-07-11
Considering the amount of problems and questions regarding samba file sharing I think there is something about Ubuntu that makes doing this very user unfriendly.  I am newbie but only in regards to Ubuntu.  I have set up samba clients and file sharing numerous times and recently did it on a SuSE box in less than 15 minutes.  I have been struggling trying to get it to work on Ubuntu for hours now.

When I go on our intranet and use a windows box I can try to map a network drive and browse the Domain and actually see the Ubuntu linux box but my shared files are not there and I can not map to it.

I have read through most of the threads and everyone seems to have a slightly different objective and/or problem and I can't see anyone that experienced this exactly.

I can't help but wonder if this is related to the added security that Ubuntu uses that forces me to type "sodu"
 practically every time I do anything. Perhaps these features are appreciated by someone at home browsing porn sites, but as a corporate developer I find am beginning to find Ubuntu annoying.

Does anyone have any idea why my linux box might show up nicely on a windows domain, but my shared folders are not present???  I used the GUI to select my shared folder(s) and set the priviledges but they are not appearing....

(sorry about the expressed frustration but I am a whisker away from prohibiting the use of Ubuntu in this company)

---

### Post by iver2435 on 2007-07-11
I wouldn't do anything rash like prohibit Ubuntu, I'm sure there's a logical explanation for your problem.

So, based on what you wrote, you have an Ubuntu file server running Samba and you're trying to connect to it using a Windows client.

Since the Ubuntu server shows up when you browse the network, that would indicate that they are in the same workgroup, and that communication between the client and server is there, so let's look at the problem from the share level.

I'm not sure what level of access you want to give out to your users and how closely you want to lock down your security, but if all you want to do is make all your shares available to everyone on your 
network, then the easiest thing to do would be to set the security level of the Samba server to "share" security.

To do this, you'll need to edit the smb.conf file where Samba pulls all it's configuration from.  Issue the following command to open smb.conf in a gedit window:

```
gksudo gedit /etc/samba/smb.conf
```

There will be a bunch of lines in there with a # in the front.  Those lines are commented and can be ignored.  The line you're going to be looking for looks like this:

security = user  

It may or may not have a semi-colon in front of it.  If it does, remove the semi-colon and change the value "user" to "share".  Save the file and you're done. 

I did this at first to get my shares working, and then I read more about Samba and how to get it running using user-level permissions.  I humbly suggest that you do the same, because it will give you more flexibility in what you allow and disallow users to access on your network.  Once you have a better handle on how Samba deals with user-level permissions, I suggest you switch it back.

Hope this helps ease your frustration!

---

### Post by madeupname on 2007-07-11
I'm not sure how you managed such a cool rational response to my rant but I think you deserve KUDOs.  Anyway, I already thought about and tried the security = shared and it didn't seem to be the magical fix.  I went as far as copying over the smb.conf file from other working linux boxes (slackware and SuSE) but that didn't seem to work either.

What I thought was odd was that in the alternate conf files that I tried WINS server was not enabled nor was a WINS server pointed to and yet the computer ID still showed up when browsing the domain.  Now that doesn't seem right to me, I believe with that configuration you should of been forced to use "NET USE" with the IP address.  It is as if the original incorrect settings are etched in stone and changing the smb.conf file and stopping/starting the samba daemon nor booting the machine seems to really change anything.......

I am not a dumb guy but I sure feel like it at the moment because I have been at this for about 3 hours trying to do what is relatively trivial on most linux distributions....

Bill

---

### Post by madeupname on 2007-07-11
I finally got this working.  I did resort to the radical approach of blowing away Ubuntu's default smb.conf file and using a preexisting working conf file from a different linux box here (which was indeed very different).  I tried this before as my last post indicated but the final change was enabling guest = ADMIN_NAME and poof everything worked.

I would have preferred getting this to work in whatever fashion the Ubuntu developers intended, but I tried for a few hours which was too long for me to spend.  Any longer and my coworkers would have mutinied.

Thanks IVER2435 for your reply...

---

### Post by iver2435 on 2007-07-11
No problem, I'm just glad it's working.

I wish you luck with all your future Ubuntu endeavors!

---

