---
title: "Dumb Question Involving Passwords"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Robster34 on 2007-01-21
I've done something really dumb. It's definitely the lowest form of Rookie mistake, by far. I just installed Ubuntu for the first time ever and I've already managed to lock myself out. On this old PC I was putting it on, it took about 8 hours for the program to install. I know it asked me for a user name and password way at the beginning, and I wrote them down somewhere, but now I can't find them. 

Please don't tell me that I have to completely re-install the whole program because I cannot get past the User Name and Password screen? (although, I would deserve it for locking myself out). I know that there is a reason why they put passwords on systems and why this is no way around them, but I had no idea that the program was going to make my login it's first priority. Especially when I'm still trying to remember what I typed in what seems like weeks ago (metaphorically).

Any ideas? I can't believe all I got to see today was a logon screen.](*,)

---

### Post by meng on 2007-01-21
Try this
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by CroEragon on 2007-01-21
Few weeks ago in similar thread we concluded that Ubuntu is very weak if your attacker have physical access, someone posted 3 or 4 methods to break into system, some of them not taking 2 minutes to do it. I cant remember procedure, but your best bet is to search forum, if you cant find anything in google put: (keywor you wanna search on forum) site:[www.ubuntuforums.org](www.ubuntuforums.org)
EDIT: Too slow...

---

### Post by Bachstelze on 2007-01-21
You don't have to reinstall, here's what to do :

At the very first screen when you boot your computer, you should have a menu offering you the option to boot in "recovery mode", choose this one instead of the normal one (if you don't see a menu, press ESC when you see "press ESC to show menu")

After a while, you should get to a root shell, just type :

```
passwd YOUR_USERNAME
```

and enter your password twice. Don't worry if you don't see little stars showing as you type, it's normal (for security reasons), just type your password and press Enter. Then type

```
reboot
```

voilà :)


**@CroEragon**, *any* system is weak when you have physical access... Except maybe if you have hard drive encryption.

---

### Post by Robster34 on 2007-01-22
I checked out the Lost Password instructions on this site and tried the Last Resort procedure. Where the instructions mention

To change your password, type passwd <username>

No matter what I try, it responds with unknown user ----------- (dashes indicate login name I've tried)

I might be screwed because I can't get the username to work either if that's what this is telling me. I just wish I could find that piece of paper or pick my own brain.:wink:

---

### Post by pebo on 2007-01-22
I remember reading in another thread that several posters somehow had duplicated their username when creating their account, so instead of 'rob' their username was 'robrob'. 
Worth a shot?

---

### Post by aysiu on 2007-01-22
How about just creating a new user, then? ```
sudo adduser *username*
sudo adduser *username* admin
reboot
``` Where *username* is the new user's name.

---

### Post by Sef on 2007-01-22
> I've done something really dumb. It's definitely the lowest form of Rookie mistake, by far.

Don't sweat it.  We all have done dumb things at times.  Just take it as a learning experience.

---

### Post by bodhi.zazen on 2007-01-22
OR

```
cat /etc/shadow
```

to list your users and see if you don't recognize one of them ...

---

### Post by Robster34 on 2007-01-22
I've decided to just completely re-install (and let it run overnight while I sleep safe in my bed). At initial set-up, now that I am paying more attention, the software only asked me for a hostname and a password. Unless it still plans on asking me for a username, maybe this is where things went wrong. I may have always known the password, but there was no first-time login name.

When I used the Last Resort method mentioned earlier, the system kept rejecting every user name I threw at it even though I was certain that I would have probably only used one of about four I always use. When I typed in passwd and left a blank space, it asked me to type in new UNIX password (?). So I did that twice and that was it. I tried to type reboot and it corrected me saying I should use shutdown command. So I tried that and it gave me directions on how to properly use shutdown. I eventually gave up and just pressed the restart button on my CPU. 

When I tried to login again, it still refused me. So now I re-install. Is there a first time generic username?

---

### Post by Immolatus on 2007-01-25
:o It would appear that you had the same issue as me as you described my delema to a tee.

however I don't feel that it was by any fault of your own, ( I have installed ubuntu into a dual boot environment on the same drive w/xppro, and it's working fine now) during my install I was never provided the opportunity to enter a username however I was provided for the password. Oddly though at one point near the end of the install I had lost any and all graphical evidence of activity (nothing on screen), and can only assume that this was the point at which one would enter said username. And I of course did not as I could not see the field. 

The point to my response however is to say that what ultimately fixed the problem was to add  a new user in recovery mode:

code: sudo adduser "name"
         sudo adduser "name" admin
         reboot

as mentioned in another reply a little bit above mine, also this wasn't half as scary as some of the other suggestions.  

Thanks guy's

---

### Post by aysiu on 2007-01-25
Since recovery mode logs you in as root, you don't need to preface your commands with *sudo*. ```
adduser *username*
adduser *username* admin
reboot
``` should suffice.

---

