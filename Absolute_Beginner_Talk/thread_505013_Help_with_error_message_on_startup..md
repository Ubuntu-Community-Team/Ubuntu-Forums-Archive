---
title: "Help with error message on startup."
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by GilesG on 2007-07-19
I keep getting this cryptic error message everytime I bootup Ubuntu. Truth be told, I have NO idea what any of it means.

I started getting it the last few times I started up, I cant remember if there was a specific program I installed first to cause this. I have only had Ubuntu installed for about 1 day prior to this. 

I am running the 64 bit version of 7.04.

the error message is posted as an attachment. The only thing I have noticed differently is now I can no longer drag around items on my desktop. I think they have something in common.

Any help would be appreciated, thanks.

---

### Post by KyleBrandt on 2007-07-19
Sounds like a problem with permissions.  First thing to check, make sure $HOME environment variable is set properly.  Type env in the terminal, somewhere in its output should be /home/yourusername.  Where yourusername is whatever your user name is:-)  If that is all fine, make sure that your home directory and that the file in your home directory (.dmrc) are actually owned by the user you are logged in.  You can find this out by going to the directory and typing "ls -l".  If you are confused just paste the output of these commands in a post here, or go and read a tutorial on linux/unix permissions.  644 is a way of describing the permissions, you can find out about this by typing "man chmod".

---

### Post by Firestorm21 on 2007-07-20
I just had mine do this to me too. I found a solution here. [http://ubuntuforums.org/showthread.php?t=491591]("http://ubuntuforums.org/showthread.php?t=491591").

It says to do:

chmod 644 .dmrc
chmod 700 ~

(I did **sudo chmod 700 /home/<account>** and it worked.)

---

