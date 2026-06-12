---
title: "params.c error"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by newborca on 2006-07-16
Hey,
 I am running Drake server (no GUI) and have been having trouble setting up samba to join my Server 2003 domain. I finally thought I had it but when I ran testparm I got the following:

params.c:Parameter() - Invalid parameter name in config file
params.c:pm_process - Failed. Error returned from params.c:parse().

I feel emberassed i can't figure this out but my smb.conf file looks good and after looking online for tips they are all programming related issues that being a newb I dont get. I don't necessarily need an answer just a point in the right direction. Its more fun that way. Thanks for the help.

newborca

---

### Post by Thenotsowyzewun on 2006-07-16
Not sure about the params.c error but have you set your samba password?

```
$ sudo smbpasswd <username>
```

Also it's my understanding that Samba can't do Digitally Signed communications, which're set to default in Windows Security Policy in Server 2003, so:

In Windows, go into REGEDIT and browse to HKEY_LOCAL_MACHINESYSTEMCurrentControlSetServicesl anmanserverparameters\ and change the vale of the key called requiresecuritysignature to 0.
Then click Start, Control Panel, Administrative Tools, Local Security Policy and browse to Security Settings\Local Policies\Security Options\ and disable the following options:
Domain member: digitally encrypt or sign secure channel data (always),
Microsoft network client: Digitally sign communications (always), and Microsoft network server: Digitally sign communications (always)

As you've probably guessed, this does make your Windows Server less secure, but it's necessary because SMB does not yet support digital signing (AFAIK - I couldn't get the machines to connect with these options enabled (as they are by default).

Hope that helps :).

EDIT: [This guy]("http://ubuntuforums.org/showpost.php?p=459070&postcount=6") had the same problem (I think) and found the solution [here]("http://ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure") (courtesy of [manicka]("http://ubuntuforums.org/member.php?u=20364")).

---

### Post by newborca on 2006-07-16
Thanks for the info. I have not set my samba password. I thought that using winbind would eliminate the need for the local passwords and authenticate with Server 2003 using kerberos. I guess just the Unix but not Samba. There is a reason I posted this on 'Absolute Beginner Talk'. I tried to set it anyway but I cannot because of the originial problem, the error in my smb.conf. As soon as I get this params.c error stuff fixed I will set it. In the meantime, I will edit ye olde server 2003 registry. Thanks for the heads up.

---

