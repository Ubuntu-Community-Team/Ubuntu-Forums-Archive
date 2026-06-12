---
title: "Share files between two computers on different domains"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by xcaos on 2007-11-28
Hi,

I'm having problems sharing files between my laptop (XP) and my desktop PC (Ubuntu). I think that the main reason is that my laptop is on my company domain and my PC is not.

All the HOWTOs explain how to configure samba for computers on the same workgroup, is there any HOWTO regarding the configuration for my scenario?

Any help would be apreciated.

Thanks

---

### Post by PeterJS on 2007-11-28
> **xcaos said:**
> Hi,

I'm having problems sharing files between my laptop (XP) and my desktop PC (Ubuntu). I think that the main reason is that my laptop is on my company domain and my PC is not.

All the HOWTOs explain how to configure samba for computers on the same workgroup, is there any HOWTO regarding the configuration for my scenario?

Any help would be apreciated.

Thanks


The difference really isn't that big, to access the XP machine from Linux when you try to login in to the share, if just using the user name on the machine doesn't work try domainname\username instead. As for going the other direction, couldn't tell you I've never configured smb on XP, or worked with a machine in a domain.

---

### Post by xcaos on 2007-11-28
SOLVED!!!

I just had to go to Places -> Connect to Server and input the information. :)

Thanks for the help

---

### Post by jflaker on 2007-11-28
> **xcaos said:**
> Hi,

I'm having problems sharing files between my laptop (XP) and my desktop PC (Ubuntu). I think that the main reason is that my laptop is on my company domain and my PC is not.

All the HOWTOs explain how to configure samba for computers on the same workgroup, is there any HOWTO regarding the configuration for my scenario?

Any help would be apreciated.

Thanks

Good that you got it.  for the benefit of others:

There are two ways to get to shares on a domain system:
Use a local account on the PC that is on the domain which contains the share, or use your domain account.  Depending on permissions, you can generally access the PC Shares.....

Non-domain PC just use a local account on the PC with the share

In both cases, the "DOMAIN" is the computer to which you are authenticating to.....on a non-domain or a domain using local accounts...the domain is the PC name

---

### Post by fiztlen on 2007-12-02
I'm having the same problem as the original poster and can't figure out what to try next.  My (work) laptop is part of a domain and I'm trying to add Samba to a windows workgroup at home.

The server is running Samba on Mythubuntu, and I can connect from either of two accounts on my wife's desktop (WinXP Home).  If I watch the log when trying connecting from my laptop it appears to translate the username properly, then reports wrong password:
```
[2007/12/02 16:50:29, 3] smbd/sesssetup.c:reply_sesssetup_and_X_spnego(1060)
  NativeOS=[Windows 2002 Service Pack 2 2600] NativeLanMan=[Windows 2002 5.1] PrimaryDomain=[]
[2007/12/02 16:50:29, 3] libsmb/ntlmssp.c:ntlmssp_server_auth(739)
  Got user=[(workUser)] domain=[(workDomain)] workstation=[(laptopName)] len1=24 len2=24
[2007/12/02 16:50:29, 3] smbd/map_username.c:map_username(155)
  Mapped user (workUser) to tweak
[2007/12/02 16:50:29, 3] auth/auth.c:check_ntlm_password(221)
  check_ntlm_password:  Checking password for unmapped user [workDomain]\[workUser]@[laptopName] with the new password interface
[2007/12/02 16:50:29, 3] auth/auth.c:check_ntlm_password(224)
  check_ntlm_password:  mapped user is: [ESPRESSO]\[tweak]@[laptopName]
```
...
```
[2007/12/02 17:06:20, 4] libsmb/ntlm_check.c:ntlm_password_check(326)
  ntlm_password_check: Checking NT MD4 password
[2007/12/02 17:06:20, 3] libsmb/ntlm_check.c:ntlm_password_check(344)
  ntlm_password_check: NT MD4 password check failed for user tweak
```
...
```
[2007/12/02 16:50:29, 2] auth/auth.c:check_ntlm_password(319)
  check_ntlm_password:  Authentication for user [workUser] -> [tweak] FAILED with error NT_STATUS_WRONG_PASSWORD
[2007/12/02 16:50:29, 3] smbd/error.c:error_packet_set(106)
  error packet at smbd/sesssetup.c(105) cmd=115 (SMBsesssetupX) NT_STATUS_LOGON_FAILURE
```

I'm also not sure what to make of this recurring message (if anything):
```
[2007/12/02 17:03:20, 2] smbd/sesssetup.c:setup_new_vc_session(1200)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.
```

I've attached my current smb.conf in case I messed up something there.  The usermap line that should be working has several permutations at the moment:
```
tweak = homeUser workUser workDomain\workUser
```

I could set up a domain at home, if that would somehow make it easier, but I'm not particularly looking for the advanced features that would add.  Trying to start simple.

---

