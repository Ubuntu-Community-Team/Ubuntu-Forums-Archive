---
title: "Creating a file server??"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by JAK4073 on 2008-01-07
I am new to linux and would like to create a home file sever with an extra PC that i have. I already installed Ubuntu 7.10  and samba. I have one more desktop and 3 wireless laptops that all run winXP pro. I would like to be able to have roaming profiles, share files/music, and printer over the server if it is possible. Like i said I am very new to linux so i really need detailed steps to show how i can do it. Also do i need to switch over Ubuntu server edition?I downloaded the regular version before  i thought about doing this.

---

### Post by dcstar on 2008-01-07
> **JAK4073 said:**
> I am new to linux and would like to create a home file sever with an extra PC that i have. I already installed Ubuntu 7.10  and samba. I have one more desktop and 3 wireless laptops that all run winXP pro. I would like to be able to have roaming profiles, share files/music, and printer over the server if it is possible. Like i said I am very new to linux so i really need detailed steps to show how i can do it. Also do i need to switch over Ubuntu server edition?I downloaded the regular version before  i thought about doing this.

File servers serve files (Linux can do that), things like Windows Roaming Profiles are only available from Windows Active Directory servers, AFAIK Linux cannot do that.

---

### Post by fuzzyeric on 2008-06-24
In spite of that, if you would like to use Local Profiles, Roaming Profiles, Mandatory Profiles, and/or Redirected Folders with Samba, see
[Samba & Windows Profiles]("http://wiki.samba.org/index.php/Samba_&_Windows_Profiles") at the [Samba Wiki]("http://wiki.samba.org/index.php/Main_Page").

---

