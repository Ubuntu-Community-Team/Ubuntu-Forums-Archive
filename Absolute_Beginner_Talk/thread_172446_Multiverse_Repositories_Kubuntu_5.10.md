---
title: "Multiverse Repositories Kubuntu 5.10"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Henaro on 2006-05-08
Well after following this guide: 
[https://wiki.kubuntu.org/AddingRepositoriesHowto](https://wiki.kubuntu.org/AddingRepositoriesHowto)
I seem to be stuck.  When I try to add the multiverse part to the end of the "universe" repository it inputs fine but when I click Apply it sets it back to "universe".  Anyone know why it is doing that and not adding multiverse?  :(to

---

### Post by revdev on 2006-05-18
Try opening up /etc/apt/sources.list in a text editor, adding the line, and then saving it.

for example, at the end of the file, type:

```
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
```
or whatever it is you're trying to add.

Then open synaptic, or at the command line, sudo apt-get update.

---

### Post by Sutekh on 2006-05-18
How about we try this from the command line?  I find those GUI tutorials too tricky.

It's very easy to do this from the command line.
  
  
Start by opening a Terminal Window - Konsole (KMenu -> System -> Konsole) and then backing up your current sources using this command
  ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` Then edit it with your preferred editor, I am using **nano** in this example.  You may prefer **kate**. If so just swap nano for gedit in the next command.
  ```
sudo nano /etc/apt/sources.list
``` When the editor opens you need to find these lines (they may have a **us.** if your in the US, etc)
  ```

  # deb http://archive.ubuntu.com/ubuntu breezy universe
  # deb-src http://archive.ubuntu.com/ubuntu breezy universe
  
  ...
  
  # deb http://security.ubuntu.com/ubuntu breezy-security universe
  # deb-src http://security.ubuntu.com/ubuntu breezy-security universe
``` You need to uncomment them - remove the # signs. This enables the universe repository. To enable the multiverse repository, add multiverse to the end of these lines.
  
  It would look something like this when you finish making the changes
  ```

  deb http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
  deb-src http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
   
  ...
  
  deb http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
  deb-src http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
``` If you save the file (Ctrl +O if you are using nano) and exit (Ctrl + X iin nano) you can then update the repositories with
  ```
sudo apt-get update
``` Then you are set, and can use Synaptic.

---

