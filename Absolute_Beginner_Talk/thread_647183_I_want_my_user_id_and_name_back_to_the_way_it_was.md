---
title: "I want my user id and name back to the way it was"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by gumpontheweb on 2007-12-22
I have read this [http://ubuntuforums.org/showthread.php?t=275035](http://ubuntuforums.org/showthread.php?t=275035)
And can't figure out what to do! 
I deleted user id 1000 which was my main user.
when I tried to put it back I get the error```
Users $HOME directory must be owned by user and not writable by others."

``` 
I have read to delete the user group that has the same name. and I found almost the same problem in this thread a day ago. 
I am sorry I cant figure this out! NOT too quick:confused:
I tried making a new user with the same name and changing the user id to 1000 int the advanced tab. All this did was add more error messages!
Can I have it the way it was?
The reason for this whole thing was because totem player wouldn't work for me but it worked for my brother, who is also an administrator, user id 1001.
please help!

---

### Post by tgilber1 on 2007-12-22
Try adding the username by using the CLI [Command-Line Interface] command adduser

[LIST=1]
[*]From GUI menu bar, click #System#Accessories#Terminal to access terminal to type the following commands
[*]sudo adduser --uid <uid-number> --gid <group-id number> --home /home/<username>
[/LIST]

ex.  sudo adduser --uid 1000 --gid 1000 --home /home/johndoe

Make sure that the uid and gid unique, meaning they are not in use in the etc files, /etc/passwd and /etc/group, respectively.

To verify, use the following command

getent passwd 1001
getent group 1001

if this command prints out info, it mean that the ids are in use.  User another id# or remove the user that has it -- as long as it is a regular user and not a system user.  Be careful, since a careless move could breach security or hose your system.

---

### Post by gumpontheweb on 2007-12-22
When I use the command sudo adduser --uid 1000 --gid 1000 --home /home/"me"
I have to enter the password but It wont let me...
I cant type anything into the terminal after?
It just doesn't let me enter the password.
I wanted this fixed since my brother didn't have ability to change permissions. I thought it was only the "owner" or user id 1000 that could?
What next???

---

### Post by taurus on 2007-12-22
Boot into recovery mode from GRUB menu and post the output of this command.

```
ls -la /home
```

---

### Post by bigken on 2007-12-22
when you type a password it does not show just try it

---

### Post by t0p on 2007-12-22
> **gumpontheweb said:**
> When I use the command sudo adduser --uid 1000 --gid 1000 --home /home/"me"
I have to enter the password but It wont let me...
I cant type anything into the terminal after?
It just doesn't let me enter the password.

You *are* typing in your password, but the terminal's set not to show it.  In terminal you don't get a string of asterisks... it's invisible!

Just type in your password and hit Enter, it'll go in fine.

---

### Post by gumpontheweb on 2007-12-22
I entered the password without seeing it and got back this:
adduser: Only one or two names allowed.
Dont ask me!
what now? 
How do I show you what happens? 	
Re: I want my user id and name back to the way it was
Boot into recovery mode from GRUB menu and post the output of this command.

Code:

ls -la /home

HOW, if nescesarry?

---

### Post by t0p on 2007-12-22
Umm, why do you want to have user id 1000?  Do you realize that an admin account can have any id, it doesn't have to be 1000?

---

### Post by gumpontheweb on 2007-12-23
> **t0p said:**
> Umm, why do you want to have user id 1000?  Do you realize that an admin account can have any id, it doesn't have to be 1000?

it doesn't have to be 1000. I thought that would make it identical? it doesn't really matter if any id # can be owner & change permissions. I don't know if it is important... is it?
I just wanted back the name and to have me as the owner.
OR, if I can change my brother to the owner and make him have unlimited access.
In my limited knowledge, I am guessing that my group name is messing with the user name, since it's the same? Am I close?
I also don't really know how to show (without just typing) the output of :
ls -la /home
I will do it and see if I can.
Thanks for being so quick to answer! you all are great!

---

### Post by gumpontheweb on 2007-12-29
Still just waiting for a solution...

---

