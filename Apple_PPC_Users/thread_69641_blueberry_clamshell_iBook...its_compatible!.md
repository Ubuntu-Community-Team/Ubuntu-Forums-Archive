---
title: "blueberry clamshell iBook...its compatible!"
date: 2005-09-27
forum: Apple PPC Users
---

### Post by urbandryad on 2005-09-27
I managed to install and run Ubuntu Linux 5.04 onto my blueberry iBook.  Its going great, some larger apps like GIMP work rather slowly though. I'm enjoying rearranging all the panels and choosing themes and stuff. :3 Learning a new OS is fun, but its funny how intuitive this already is.

Eventually, I'm going to tackle learning more about terminal. :3

Just wanted to let clamshell owners know how it went.

If you don't have a battery in your iBook, you need to run terminal to change your hardware clock settings or Nautilis won't run. I did F1-Command (or was it option? Can't remember which) to open virtual terminal. Login as root.

For date I did

hwclock --set --date="mm/dd/yyyy" 

I haven't figured out how to add the time in yet. I thin it goes between the "'s as 00:00:00 (hour:min:sec)

in root I didn't need to use sudo, but I couldn't use SUDO in my USER account. Weird huh?

---

### Post by DJ_Max on 2005-09-27
Glad to see someone taking the initiative to learn things.

About the root issue, did you manually create a root account? As I don't know what you mean when you say "in root" as by default Ubuntu doesn't have one.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by urbandryad on 2005-09-27
I guess so. When I login to terminal I put

username: root
password: password

I can't remember what step this is. I don't ever recall creating a root user. Only my own user. root shows up with a % in it. ^^

Or is it root terminal I'm talking about? Dunno, this is all new to me?

---

### Post by urbandryad on 2005-09-27
actually, I remember creating a password for root during installation, so maybe root is the name I gave to the ubuntu system? hmm

---

### Post by stuporglue on 2005-09-27
The otherday I chose some funny install options and had to go back, and somehow ended up in the Debian installer. I had to set a root password there, and sudo didn't work afterwards either.

So, those options are still there somewhere. :-)

---

### Post by DJ_Max on 2005-09-27
Ahh, probably. Because Ubuntu doesn't ask for a root account. Looks like you have a username conflict.

---

### Post by urbandryad on 2005-09-27
username conflict? I don't understand. I asked me for an administrator password for root during install, and I made one, and thats how I logged into terminal with root. And I created my user account urbandryad with a different password during install. How is there NOT a root account? That option came up both times I installed.

---

### Post by urbandryad on 2005-09-28
*comes back*yeah, you were right. Some sort of root problem. Apparantly my user account isn't an administrative account, and when I want to run anything like synaptic or add users it asks for an administrative password, and regardless of what I put in, it won't run, it tells me I need to be in an administrative account, but I can't log into ubuntu using root anyway, cause its says administrators cannot login from the login page. Okay. So how do I fix this? Help? :(

---

