---
title: "Restore X after changing permissions of $HOME"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by Phelan on 2007-10-04
So I was trying to save something in my gtkrc-2.0 to get the icon transparency to work.  I believe i modified the permissions of the home/xxx/ folder to where anyone could write it, as well as the gtkrc-2.0 file itself.  It then let me save my modifications and I logged out.

As soon as I logged back in, i noticed my user picture was gone, and i immediately got an error message about the home folders permissions weren't allowed and the user wouldn't be loaded normally.  I got back into xubuntu and tried to undo what I did.  I changed the permissions back and loaded gtkrc and it hadnt saved correctly anyway.  I logged in an out 2 more times trying to fix it.

I then rebooted the system, only to be greeted by a command line.  I can post the error message if needed, I am just in windoze right now.

have no idea what to do :)

Was thinking of wiping the partition out and going with puppy, zenwalk or even fluxbox, but I really like the support and programs for ubuntu/xubuntu.  This newb needs help!

---

### Post by mrazster on 2007-10-04
When you are in CLI try doing this:
```
chmod 766 /home/name_of_your_home_folder
```

if that doesn't work...then try

```
chmod 777 /home/name_of_your_home_folder
```

Not sure if you have to use ***sudo*** in front of the commands....but it'll tell you if you have to or not.

---

### Post by steevols on 2007-10-04
I agree, you need to restore the permissions. I don't usually think that messing with home-director permissions is a good idea, as a lot of programs use the home-directory to store settings.

Also, you'll have the same problems if you tried doing this sort of thing in any other Linux that used GDM.

---

### Post by bodhi.zazen on 2007-10-04
Please use a more appropriate and descriptive title for your threads. I almost moved this to the cafe or backyard as it appears to be flame bait and not a support question.

Title updated ...

---

### Post by Phelan on 2007-10-04
> **bodhi.zazen said:**
> Please use a more appropriate and descriptive title for your threads. I almost moved this to the cafe or backyard as it appears to be flame bait and not a support question.

Title updated ...

Sorry, that was not intended.  Wasn't sure what to put.

---

### Post by Phelan on 2007-10-04
> **mrazster said:**
> When you are in CLI try doing this:
```
chmod 766 /home/name_of_your_home_folder
```

if that doesn't work...then try

```
chmod 777 /home/name_of_your_home_folder
```

Not sure if you have to use ***sudo*** in front of the commands....but it'll tell you if you have to or not.

So i tried this, and it says invalid login.  I assumed I had to login so I typed my user/pass, then did the chmod again.  Still same respond, invalid login.

---

### Post by mrazster on 2007-10-05
> **Phelan said:**
> So i tried this, and it says invalid login.  I assumed I had to login so I typed my user/pass, then did the chmod again.  Still same respond, invalid login.

Just to clarify...did you change the line ***name_of_your_home_folder*** to the actual name of your home folder..? ..if so then try doing this first:

```
sudo chown username /home/name_of_your_home_folder
```

and then try doing the chmod thing again.

---

### Post by Phelan on 2007-10-05
Still can't get it to do anything, all it will say is invalid login.  Let me clarify so we can understand each other and my problem better.

The name of my user is "cole".  The name of the computer is "laptop".  When it command line loads, it says "cole-laptop login:".  I start by inputting "sudo chown cole  /home/cole".  It prompts for password and then says invalid login.  I've tried the chmod commands as well, with and without 'sudo'.  I also tried typing "cole" and then it prompts for password, comes up with something about no warranty with ubuntu and says at the bottom "cannot cd to /home/cole/".

Hope this helps.  Running windows for the past day makes me really appreciate ubuntu!  Hope I don't have to redo it i just got it setup to where i am extremely happy with it and have everything working.  :(:confused:](*,)

EDIT:  I have no idea but if this matters, but the ORIGINAL install is 7.04 ubuntu, I have just added xfce too it and was logged in as an xfce session not a gnome session when I messed it up, it is NOT a pure xfce only install.

---

### Post by RedSquirrel on 2007-10-05
On the console, where it says "login: ", you have to type in your username, which is **cole**. Then it will ask for your password. Since you don't have appropriate permissions for your home directory, it cannot change to that directory. That's what the "cannot cd to /home/cole/" means.

Try this to fix things: when you boot the computer, try selecting the **recovery mode** and run the commands there. Recovery mode should be one of the options in your grub menu. 

When you are done running the commands, press Ctrl-Alt-Delete to reboot.

EDIT: The default permissions (when you first install) are 755.

---

### Post by Phelan on 2007-10-05
Ok, just tried this.  Loaded up in recovery and did both chown and chmod commands.  After each one the cli says nothing in response, just blank after you enter the command.  I then restarted and it did the same thing.  I logged in as you said, and tried commands in there again, only to get "invalid login" after each one.

:confused::confused:

---

### Post by RedSquirrel on 2007-10-05
When you run the chown and chmod commands there is no output. That's normal.

In recovery mode, if you run the commands:

```
 chown cole:cole /home/cole
```and then

```
 chmod 755 /home/cole
```That should set things the way they were when you first installed. 

Try the following command to see if things are fixed:

```
ls -ld /home/cole
```It should report something like this:

> [COLOR=Blue]drwxr-xr-x[/COLOR] 51 [COLOR=Blue]cole cole[/COLOR] 12288 2007-10-05 07:53 /home/cole
If that still doesn't help, can you go into recovery mode and run the following command and post the output:

```
ls -ld /home/cole
```

---

### Post by Phelan on 2007-10-05
Tried that now.  In normal boot mode, it does the same thing..login incorrect.  In recovery mode its the same, no response like normal.  What's returned from ls -ld /home/cole/ is the same in both recovery and non.

---

### Post by Phelan on 2007-10-05
will post results of ls -ld from recovery mode when i get off work 6am tommorow.

---

### Post by mrazster on 2007-10-09
Did you get your problem sorted..?

---

### Post by Phelan on 2007-10-09
Nope, still only boots to CLI.  Any ideas?

---

### Post by Phelan on 2007-10-12
*bump*

---

### Post by RedSquirrel on 2007-10-12
> **Phelan said:**
> will post results of ls -ld from recovery mode when i get off work 6am tommorow.
bump :)

---

