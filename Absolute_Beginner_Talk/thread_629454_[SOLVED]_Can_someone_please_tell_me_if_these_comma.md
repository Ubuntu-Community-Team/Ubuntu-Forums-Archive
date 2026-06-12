---
title: "[SOLVED] Can someone please tell me if these commands will do what I want them to?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by tomsa on 2007-12-02
A few days ago, I tried doing the HOWTO: Thumb Buttons Tutorial located here:

[http://ubuntuforums.org/showthread.php?t=3828]("http://ubuntuforums.org/showthread.php?t=3828")   

I somehow screwed this up, and my scroll wheel is now a forward/back button. Everything else seems to be working fine, though.  Naturally, being a big linux noob, I didn't understand the severity of editing my xorg.conf file, and didn't make a backup. I would like to undo what changes I have made and stick with the default configuration (so that I can have my scroll wheel back), but I am not quite sure how to get back to it. I'm pretty sure that Ubuntu has created a backup for me (xorg.conf~) but I'm not sure. As I know just enough to be able to really wreck up my computer at the command line, I'd like to get your opinion on if this will work or not:

1. Remove imwheel through synaptic
2. run the command "sudo rm /etc/X11/Xsession.d/57xmodmap"
3. run the command "sudo rm /etc/X11/imwheelrc"
4. run "dpkg-reconfigure xserver-xorg"
5. reboot and hope it worked
6.  If it didn't work, use "sudo gedit /etc/X11/xorg.conf~"  to open up the backup file, and rename xorg.conf~ to xorg.conf to over write what I had been messing with
7. reboot and hope it worked

should that do it, or will I just screw up my computer even worse?

Please help!](*,)
__________________

---

### Post by p_quarles on 2007-12-02
Without knowing *exactly* what is in those files (since I don't have either of them on my system), it looks like that procedure will revert your Xorg back to the default configuration. 

A few suggestions, though. Since you've learned your lesson about backing things up, it's time to start putting it into practice. Instead of using "rm," just rename those files:
```
sudo mv /etc/X11/Xsession.d/57xmodmap /etc/X11/Xsession.d/57xmodmap.bak
sudo mv /etc/X11/imwheelrc /etc/X11/imwheelrc.bak
```
Then, step number 4 will require root, so use "sudo" with that command.

Finally: In step 6 don't use "sudo" with gedit. For graphical programs, there's a special way of invoking root:
```
gksudo gedit /etc/X11/xorg.conf~
```

---

### Post by tomsa on 2007-12-02
> Without knowing exactly what is in those files (since I don't have either of them on my system), it looks like that procedure will revert your Xorg back to the default configuration.


That is exactly what I am trying to do- so that's good news!

I have a question about the following instructions:
> 
A few suggestions, though. Since you've learned your lesson about backing things up, it's time to start putting it into practice. Instead of using "rm," just rename those files:
Code:

sudo mv /etc/X11/Xsession.d/57xmodmap /etc/X11/Xsession.d/57xmodmap.bak
sudo mv /etc/X11/imwheelrc /etc/X11/imwheelrc.bak

 

In the original Howto that I used, I had to make those files executable.  If I simply move them, do they remain executable and continue to affect my system?  Do I even need them if I remove imwheel?  Their contents are as follows (please forgive the extensive quote from the original howto, I just want to provide all pertinent information):  

> Step 3: Creting the imwheel config file

    Create a file called /etc/X11/imwheelrc using your favorite text editor, in this case, nano:
    Code:

    $ sudo nano /etc/X11/imwheelrc

    and put this text in it:
    Code:

    ".*"
    None,Up,Alt_L|Left
    None,Down,Alt_L|Right

Step 4-1: Configuration for GDM, KDM, and XDM

    If you don't use GDM, KDM, or XDM (if you log in through a graphical interface, you DO use one of these), skip this step. If you do, create a file called "57xmodmap" in /etc/X11/Xsession.d/:
    Code:

     sudo nano /etc/X11/Xsession.d/57xmodmap

    and put this code in it:
    Code:

    #/bin/bash
    xmodmap -e "pointer = 1 2 3 6 7 4 5"

    Save the file and then change the permissions so that it can be executed:
    Code:

    sudo chmod 777 /etc/X11/Xsession.d/57xmodmap

    To explain the naming convention, the number at the beginning tells the xsession when to load a process. If you list the contents of /etc/X11/Xsession.d/ you'll notice that the file starting with 60 is the imwheel script. It was automatically created when installed. We need the xmodmap to run before that, so I chose 57. Now log out and log back in to get everything working. You should now be able to use the forward and back buttons (or just the back button, depending on how many buttons your mouse has). Log out and log back in to see the changes

If I don't remove those files, don't I need to make them so they are no longer executable after I move them? (I'm not quite sure how to do that, I was just copying and pasting code at that point- I have a good bit more command line study to do) Thanks again for your continued assistance!

---

### Post by p_quarles on 2007-12-02
Renaming them won't change the permissions on those files, but it doesn't matter. Xorg is looking for files with specific names, and if you add ".bak" to the end of those files, it will no longer return a match.

---

### Post by tomsa on 2007-12-02
That good to know- thanks for the help.  I'll try this out and see if it works as soon as I can get everything backed up!

---

### Post by tomsa on 2007-12-03
It worked!  My scroll wheel is back!  Thanks so very much for the help.  I must say, I was a little intimidated by linux when I first started using it, but there are so many resources available, and so many helpful people on these forums that it really hasn't been hard at all!  I'm finally starting to feel a good bit more comfortable with the command line, and actually wondering why it scares people.  It really makes it so you can do what you want with your machine.  It's been awesome to see that I was mostly right in my approach to fixing my problem.  Thanks again!

---

### Post by p_quarles on 2007-12-03
Glad to help. Yeah, the command line can be awesome. It's initmidating at first because there's so much to know, but it's ultimately far more flexible than a pre-fab GUI app could ever be. 

By the way, you can mark this thread as "solved" using the "thread tools" button at the top. That way, when people run searches on similar issues, they'll see that this thread contains a solution.

---

