---
title: "Password-less UBUNTU"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by ashrack on 2005-12-04
Since am the only one using UBUNTU and not 4 any serious work ATM, since am still learning it. I would like a way to remove those constant prompts for PASSWORD. I would like to have a password-less sistem. I know this is totally insecure but please bare with me.

---

### Post by tonysathre on 2005-12-04
i dont think that is possible since ubuntu prolly wouldnt allow such an insecure system

---

### Post by erikpiper on 2005-12-04
But is it connected to the internet? If so, that would be suicide.
Just bear with them ;)

I could tell you how- but it is a TERRIBLE idea!

---

### Post by ekarni on 2005-12-04
System -> Admin -> Login screen setup will let you auto-login a user at startup.  

Once you've got the system mostly setup and aren't using Synaptic, sudo, etc. every 10 minutes the password typing goes waaay down.  Hang in there!

---

### Post by erikpiper on 2005-12-04
the problem with that is it makes switching window managers harder!

---

### Post by Kvark on 2005-12-04
It is not only about users but also about programs. When Synaptic attempts to install something, how does the system know that you the user told Synaptic to do that? What if a virus would attempts to install itself, how would the system know that you the user did not ask the virus to do that?

When your password is required to install something it's impossible for a program to do it without approval from the user since only the user knows the password.

---

### Post by Iandefor on 2005-12-04
I agree with Kvark, ecarni and erikpiper. 
However, I'll tell you how with the following disclaimer: "You have been warned by people on this forum that this is unsafe and should not be done. Having warned you, we are not liable for anything bad that happens to your computer because of us giving you the information to do this."

Ok, here goes. Open up the login screen manager, open up the security tab, and check "Allow root to log in with GDM," and MAKE ABSOLUTELY SURE that the option is unchecked for "Allow root to log in remotely with GDM,"-that isn't related to logging in automatically, it's just plain insecure. I'm not telling you how to make your system any more insecure than you already want it :). With that done, go to "users" tab and add root to the include list. Click apply. Now, head back to the "General" tab, and check "Log in a user automatically after a specified number of seconds" and select root. Set it to either 0 or 1 seconds. I'd go with 1.


I imagine this would work. If not, that's just Linux being secure at you. The necessity for doing something with root priveleges should go down after you get it all set up, as ecarni said. If you need to set the root password, you can do that via the users and groups dialog.

---

### Post by ashrack on 2005-12-05
@LANDEFOR
I've already done this prior to starting this thread.
But I still can't get the root under:[QUOTE=Iandefor]Now, head back to the "General" tab, and check "Log in a user automatically after a specified number of seconds" and select root. Set it to either 0 or 1 seconds. I'd go with 1.[/QUOTE]

@ALL
Just thought about it a little and being a root it's not very good. Not so much becouse of security. But because if U fuxar a user account no problem ROOT can fix everything, but if U fuxar a ROOT account. Then that means trouble.
But what I would still like to have is the following:
When I log on as a user I really hate that I have to type a password everytime I lunch eg. Synaptics Package Manager, or the KEYRING feature
Could this be disabled?

---

### Post by UbuWu on 2005-12-05
[QUOTE=ashrack]
Just thought about it a little and being a root it's not very good. Not so much becouse of security. But because if U fuxar a user account no problem ROOT can fix everything, but if U fuxar a ROOT account. Then that means trouble.
But what I would still like to have is the following:
When I log on as a user I really hate that I have to type a password everytime I lunch eg. Synaptics Package Manager, or the KEYRING feature
Could this be disabled?[/QUOTE]

In the /etc/sudoers file, it is possible to disable the need for a password for certain programs. E.g. you could eliminate the need for a password for synaptic but still not have all the dangers of logging in as root. Type man sudoers at the terminal for more info. Btw. you should edit the sudoers file with visudo for additional safety.

---

### Post by ashrack on 2005-12-05
Tried "man sudoers" but don't understand anything its written there and thus I have no idea what to change in:
"sudo visudo"
COuld U help me out here?
the username is "tom"

---

### Post by tonysathre on 2005-12-05
dont know if this is possible but maybe try writing a script that will automatically insert your password anytime you are prompted for it, this would still keep the security aspects but would eliminate having to manually typing it in, how to do this i have no idea

---

### Post by Gray. on 2005-12-05
[Clicky]("http://www.ubuntuforums.org/showthread.php?p=546804#post546804")

---

### Post by ashrack on 2005-12-05
[QUOTE=Gray.][Clicky]("http://www.ubuntuforums.org/showthread.php?p=546804#post546804")[/QUOTE]
That isn't the case 4 me

---

### Post by amohanty on 2005-12-05
Another way:

```
sudo passwd
```

provide the password and that effectively sets up the root user for you.

No open up a terminal and type:
```
su
```

provide the password you setup in step 1 and then launch all sudo related things from the term. If you dont know what command to use for a launcher in the menu, open up menu editor navigate to the item and right click to get properties and go.

Just dont forget to logout of the terminal by hitting Ctrl-d

Please remember that all the methods suggested here are insecure for a number of reasons and should be avoided as far as possible.

AM

---

### Post by ssam on 2005-12-05
you could use
```
sudo su
```
to get a root shell and work from their.

or set sudo not to require a password in the sudoers file

---

### Post by ashrack on 2005-12-06
Ive set sudoers so the sudo no more reguires password.

---

