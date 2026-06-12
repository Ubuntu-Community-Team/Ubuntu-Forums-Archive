---
title: "what happened??????"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by mszl_1 on 2005-12-15
im using fedora core 4 at the moment all be it i ned to replace my modem and printer and cant choose to keep with fedora or swap to ubuntu either way i like what i see in linux. here's my question. i installed ubuntu last night and tried to look at installing additional programs. it allowed my to view the options available OK but this morning when i wanted to refresh my poor memory in regards to what is available it refused my root password and hence i could not view the options. why is this?did i change someting accidently or is this a common issue?
thanks

:confused:

---

### Post by 23meg on 2005-12-15
The root account is disabled by default in Ubuntu, so if you didn't create one on purpose, you don't have a root password. For administrative tasks you're supposed to use your user password with sudo or gksudo.

---

### Post by mszl_1 on 2005-12-15
thanx 23meg. i created a root password but it still blocks me! could it be that i went to synaptic manager to install add ons and so "break?" the ability to add additional packages?

---

### Post by nocturn on 2005-12-15
[QUOTE=mszl_1]thanx 23meg. i created a root password but it still blocks me! could it be that i went to synaptic manager to install add ons and so "break?" the ability to add additional packages?[/QUOTE]

I have never experience this.  
Is your logged in user a member of the admin group?  If so, you should enter the password for that user to start synaptic.

---

### Post by mszl_1 on 2005-12-15
thanx nocturn, 
not sure will have a look tho. considering the ease of reinstalling i might do this and see if this makes a difference.

---

### Post by Knomefan on 2005-12-15
[QUOTE=mszl_1]thanx nocturn, 
not sure will have a look tho. considering the ease of reinstalling i might do this and see if this makes a difference.[/QUOTE]

I don't know if I understand you correctly, but you'll have to use your users password, not the root password to log int synaptic. (at least if you start it from the menu, that is)

---

### Post by 23meg on 2005-12-15
Knomefan is right; if you still can't get anything running with your user password, post the contents of your /etc/hosts file, along with the errors you're getting.

---

