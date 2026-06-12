---
title: "How to log in as Adminstrator"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by New_Tux on 2005-11-24
I know my password but what username am I supposed to input?

---

### Post by linbetwin on 2005-11-24
Could you be more specific?

If you mean at the login screen, type in YOUR user name, the one you created when you installed Ubuntu.

Are you referring to something else?

---

### Post by SuperMike on 2005-11-24
[QUOTE=New_Tux]I know my password but what username am I supposed to input?[/QUOTE]

The "administrator" account on Linux and Unix is called "root". However, in Ubuntu, by default, they have disabled the ability to login as "root" because they want to help you protect the OS from getting messed up. You may know that in the world of system administration, it's easy to screw things up if you always login as root. Instead, they want you to consciously login as another user ID and then, if you need root capabilities, open a command prompt and put "sudo" in from of your command, as in:

sudo vi /etc/hosts

Next, sometimes when doing something in the GUI under your regular user ID, Ubuntu may pop a dialog up asking you to put in your password. This is normal.

Next, there's a way to enable root to login on your workstation. Just do this from a command prompt:

sudo passwd root

Once you have done this, you can now log out and back in again as root. That's what I have done on my system at home and at the office because that's just how I like to live.

---

### Post by New_Tux on 2005-11-24
[QUOTE=linbetwin]Could you be more specific?

If you mean at the login screen, type in YOUR user name, the one you created when you installed Ubuntu.

Are you referring to something else?[/QUOTE]

Yes I can long into the username created when I installed Ubuntu.  However I am not allowed to create files in the file system.  I don't have permission.

---

### Post by 23meg on 2005-11-24
You can only create files in your home directory by default. Prefer your home directory to store personal documents; consider the rest of the file system as belonging to the system. If you have to create something elsewhere, append "sudo" as a prefix to the command you use to create it.

---

### Post by New_Tux on 2005-11-24
sudo passwd root

Once you have done this, you can now log out and back in again as root. 

Okay I have made it this far but where am I supposed to log in from?  You can't log in from the normal log in area?

---

### Post by 23meg on 2005-11-24
You can't by default, and you shouldn't. Don't use the root account, use sudo with your normal user account instead.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by odin on 2005-11-24
[QUOTE=New_Tux]sudo passwd root

Once you have done this, you can now log out and back in again as root. 

Okay I have made it this far but where am I supposed to log in from?  You can't log in from the normal log in area?[/QUOTE]

I sugest you to do what people said in other posts but the answer to your question is that you have to allow root to login in gnome.With your normal user go to System->Administration->configuration of the login screen(well this a tranlation but gess you can find it,it's one of the first option in the menu)

Then go the security tab and select the "allow administrator user to login in gdm".Then you'll be able to login as root.Anyway you shouldnt,you can do everything you want with your user and sudo.

---

