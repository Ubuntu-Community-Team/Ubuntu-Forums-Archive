---
title: "Unable to cd /Home/user"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by Nameless on 2005-12-28
This is a continuation of my previous thread here: [http://ubuntuforums.org/showthread.php?t=108975](http://ubuntuforums.org/showthread.php?t=108975) because am still completely at a loss, but I don't think my other thread actually describes what I've done and I've not been able to find anything on google or any other forum.  

I'm having trouble booting up.  When I enter my user name and password, I get the following error:  "unable to cd /home/nate" where "nate" is my user name.

I'm thinking this is a permissions problem, so here's what I've done: 

I booted up in recovery mode (using the 686 kernel)
I get the following prompt: root@jnddesktop~#: 
At the prompt, I'm able to enter "startx" and boot into a verson of gnome.  

As gnome boots up, I get the his message:  "Failed to initialize HAL!" 

1) What is HAL?  Does this matter?  Is that normal for recovery mode? 

I'm able to close the above message dialoge box.

I enter my file system to check the permissions and I checked the following: 

/Home - Owner: root, Group: root, -rwxrwxrwx
/Home/Nate - Owner: nate, Group: root, -rwxrwxrwx
/Root - Owner: root, Group: root, -rwx------

2) Ok, so I think my permissions are set up correctly, but I still can't seem to get the system to log me on correctly.   Do I have the right permissions? 

I'd really like to avoid a reinstall, but I have no idea what to do next. Any help is appreciated.  Thanks.

---

### Post by Kimm on 2005-12-28
I got a smiliar problem a while back, for some reason I think / itself had the wrong permissions, I solved it by doing chmod <something> /, but I cant remember what <something> is.

---

### Post by Nameless on 2005-12-28
If I am able to enter gnome and change the permissions on my file system, is that the same as using chmod on the terminal?  I was thinking that it was chmod is the permission command....right?

---

### Post by invisage01 on 2005-12-28
correct.. the gnome permissions is the same thing as the chmod sorta stuff..

---

### Post by Nameless on 2005-12-28
Well, I tried this : ```
chmod a+wrx / -R 
``` and it worked.  

What am I going to need to be worried about if all users have all access to every drive?

---

### Post by cwaldbieser on 2005-12-28
[QUOTE=Nameless]Well, I tried this : ```
chmod a+wrx / -R 
``` and it worked.  

What am I going to need to be worried about if all users have all access to every drive?[/QUOTE]
That is not really a state the system ought to be in.  I would suggest that you back up all your important data and reinstall.  You should probably get some other opinions, though.

---

