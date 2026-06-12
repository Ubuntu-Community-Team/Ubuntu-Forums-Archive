---
title: "[SOLVED] Loggin in as Root in GUI"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by OldNewb on 2008-02-26
I would like to start by saying that I am a fairly new user and am learning how to live in the world of Linux.  That being said I know that it is a bad idea to just run as root as I could wreck my machine.

That being said on the rare occasion that I do need to use root is it possible to login as root with the GUI.  I ask because as a windows convert I find a GUI easier to use and clamAV does not want to update without being root but does not ask for my password.  

Thanks for the help.

---

### Post by p_quarles on 2008-02-26
A) Running the entire GUI as root is asking for trouble. Completely apart from any security issues, that's doing something the system wasn't designed to do, and carries a high risk of ruining your normal user's permissions settings.

B) Running individual GUI applications as root is fine. You can do this by using the "gksudo" command to launch the application:
```
gksudo nautilus
```
for instance, will launch your file manager with full root permissions. You can either run these applications from the terminal, or create separate launchers for them in your menu/panel/dock.

---

### Post by aysiu on 2008-02-26
> **OldNewb said:**
> 
That being said on the rare occasion that I do need to use root is it possible to login as root with the GUI.  I ask because as a windows convert I find a GUI easier to use and clamAV does not want to update without being root but does not ask for my password.   There is no rare occasion you **need** to log in as root.

You can use the GUI and assume temporary root privileges with *gksudo*. If you don't want to keep typing *gksudo*, create a launcher for it. I'm not sure what the command is for clamAV, but if it were *clamav*, you'd create a launcher or keyboard shortcut for ```
gksudo clamav
```

---

### Post by bodhi.zazen on 2008-02-26
Wow, the mods are all over this one :)

And, for completeness, the classic links :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by stchman on 2008-02-26
> **OldNewb said:**
> I would like to start by saying that I am a fairly new user and am learning how to live in the world of Linux.  That being said I know that it is a bad idea to just run as root as I could wreck my machine.

That being said on the rare occasion that I do need to use root is it possible to login as root with the GUI.  I ask because as a windows convert I find a GUI easier to use and clamAV does not want to update without being root but does not ask for my password.  

Thanks for the help.

Yes running as root is a very bad idea.  Also there is no need for an AV in Linux unless you email a lot to your Windows friends.

If you must you can install AVG for Linux and run it as root using the following command:

```
gksudo avggui
```

---

### Post by aysiu on 2008-02-26
> **stchman said:**
> Also there is no need for an AV in Linux unless you email a lot to your Windows friends. Even if you email a lot of your Windows friends, I still don't see the need for AV, unless you're sending them strange attachments (why would you do that?).

Anti-virus in Linux is most appropriate if you are running a mail server or a file server that also serves Windows computers. Otherwise, it is just a waste of space and resources.

---

