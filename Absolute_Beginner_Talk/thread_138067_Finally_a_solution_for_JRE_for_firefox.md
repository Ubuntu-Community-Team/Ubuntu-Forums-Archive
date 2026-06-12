---
title: "Finally a solution for JRE for firefox"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by daredevil on 2006-03-01
I had hard times with getting jre work with firefox. Finally i came across this article and it really works great.

```
http://www.debian-administration.org/articles/142
```

---

### Post by nickpaton on 2006-06-17
I can confirm that Dardevil's post does work, but does need some changes for Dapper.

First of all, I did originally post the changes which were minor file differences, and did work until I installed Flash as well, which then broke the symbolic link for Java.

The procedure that has worked for me is to delete the symbolic links for both Java and flash 

For Java search for libjavaplugin-oji.so, and navigate to that folder:

cd /usr/.../... to the folder

Login as root:

 sudo su

and remove the plugin link:

rm libjavaplugin-oji.so

In synaptic search for jre and remove sun-java5-bin and -jre files.

For Flash search for flashplayer.xpt and libflashplayer.so and similarly delete as above.

The correct order is to install Java first, followed by Flash as follows.

Java:

Back into Synaptic and install the two jre files as above.

To carry out the symbolic link refer to the instructions in post:

[http://www.ubuntuforums.org/showthread.php?t=179606&highlight=firefox+java](http://www.ubuntuforums.org/showthread.php?t=179606&highlight=firefox+java) 

 Flash:

Referring to my post in [http://www.ubuntuforums.org/showthread.php?t=193870&highlight=flash](http://www.ubuntuforums.org/showthread.php?t=193870&highlight=flash)

Download Flash from:
[http://www.adobe.com/shockwave/downl...ShockwaveFlash](http://www.adobe.com/shockwave/downl...ShockwaveFlash)

and save in your Home folder.

Uppack and uncompress:

tar -xzf install_flash_player_7_linux.tar.gz

Open Terminal and Login as root:

sudo su

Navigate to newly created "install_flash_player_7_linux" folder in your Home directory:

cd /install_flash_player_7_linux

Then to install:

./flashplayer-installer

Respond to various questions and when prompted where to install, and accept the folder offered.

This will automatically carry out the correct symbolic linking.

Hopefully this will correctly install both Java & Flash without one upsetting the other.

(Modified to incorporate setting up both Java & Flash)

---

