---
title: "Alien is giving me some problems"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by craniumsoftener on 2007-10-02
Hello folks,

I have an rpm file that needs to be converted to a deb file.  I installed alien and tried it out.  This is the result:

philip@philip-laptop:~$ sudo alien  stardict-cdict-gb-2.4.2-1.noarch.rpm
File "stardict-cdict-gb-2.4.2-1.noarch.rpm" not found.

I checked the name several times.  Does the original file have to be in a particular place?  (It is on the desktop now.)  Is there something else going on?

Thanks in advance

---

### Post by mevets on 2007-10-02
> 
cd ~/Desktop

before alien

---

### Post by craniumsoftener on 2007-10-02
Thanks.  It seems like a good idea, but I tried it, and it didn't work.

---

### Post by bumanie on 2007-10-02
in terminal try cd /home/"your name" (ie name of home folder)/Desktop.
Then try alien. 
I have found the above command  works for me if trying to install something downloaded to the desktop.

---

### Post by craniumsoftener on 2007-10-02
Thanks for your input.  May I ask is this what you had in mind?

philip@philip-laptop:~$ cd /home/philip/Desktop
philip@philip-laptop:~/Desktop$ sudo alien stardict-cdict-gb-2.4.2-1.noarch.rpm
Password:
File "stardict-cdict-gb-2.4.2-1.noarch.rpm" not found.
philip@philip-laptop:~/Desktop$ 

Unfortunately, it didn't work.  Perhaps I did something wrong?

---

### Post by BLTicklemonster on 2007-10-02
sudo alien ~/stardict-cdict-gb-2.4.2-1.noarch.rpm

---

### Post by bumanie on 2007-10-02
That is what I had in mind. I am fairly new to Ubuntu and haven't really had time to try much until the last fortnight. In the past I have seen instructions such as cd~ Desktop such as mevets recommended. It never worked for me either. That is why I suggested the other command line. I tried that the other day and it worked wheres just cd~ Desktop did not work.
Have you installed alien via apt-get?

Try this, but insert your files's name where it mentions avg....
$sudo apt-get install alien

Example

Suppose we have a avg antivirus avg71lms-r30-a0782.i386.rpm file

To convert .rpm to debian

$sudo alien -k avg71lms-r30-a0782.i386.rpm

Now you should be having avg71lms-r30-a0782.i386.deb file

To install .deb file

$sudo dpkg -i avg71lms-r30-a0782.i386.deb

If you don’t use -k option you should see avg71lms_r30-1_i386.deb file the difference is it will add 1

Hope this helps.

---

### Post by stchman on 2007-10-02
> **craniumsoftener said:**
> Hello folks,

I have an rpm file that needs to be converted to a deb file.  I installed alien and tried it out.  This is the result:

philip@philip-laptop:~$ sudo alien  stardict-cdict-gb-2.4.2-1.noarch.rpm
File "stardict-cdict-gb-2.4.2-1.noarch.rpm" not found.

I checked the name several times.  Does the original file have to be in a particular place?  (It is on the desktop now.)  Is there something else going on?

Thanks in advance

You need to specify the path.  ~/Desktop is the path to your desktop.

Do the following:

```
sudo alien --scripts --keep-version -d ~/Desktop/stardict-cdict-gb-2.4.2-1.noarch.rpm
```

I always use the --scripts and the --keep-version.

---

### Post by craniumsoftener on 2007-10-02
Thanks so much for the help.  I tried it.  The same bad result.  I used Synaptic Package Manager to download it, so it should be legit.  Strange.  Perhaps if I sleep on it, the answer will come.

---

