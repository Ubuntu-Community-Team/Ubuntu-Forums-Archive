---
title: "avoid reinsert your repositories dvd"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by stagos on 2007-11-27
The easy way to avoid re-insert your repository DVD
Case :
You have 5 Ubuntu 7.10 repo DVD, and you're boring to re-insert the dvd. Maybe this simple tutorial can help you out.

Requirement :
1. Ubuntu 7.10 on your computer
2. 5 DVD from Ubuntu 7.10 repository
3. 20 GB of hard disk
4. Yourself

Action:
1. Insert your repository DVD to your DVD Rom, and let Ubuntu read it, after while you will see on your screen a message box like below, that inform you, Ubuntu detect a repository cd, and will add the list to it repos database.
[IMG]http://akakom.org/~andec/tutor/repo-dvd_files/Screenshot-Software%2520packages%2520volume%2520detected.png[/IMG]
click 'start package manager" button.And repeat this step to another 4 repo DVD all 5 DVD.
[IMG]http://akakom.org/~andec/tutor/repo-dvd_files/Screenshot-Synaptic%2520Package%2520Manager.png[/IMG]


2. After 5 DVD repo database update to package manager database. Then start copy the 5 DVD + the installer CD to your hard drive (min. 20 GB), in this case I will save it on different partition called /gudang on /dev/hda2. When we copy the DVD, we will save it into ISO file.First insert the DVD on the DVD-drive then on the desktop icon, right-click on DVD-drive icon.
[IMG]http://akakom.org/~andec/tutor/repo-dvd_files/Screenshot-Desktop.png[/IMG]
choose copy disc menu, then you will find a dialog box like this
[IMG]http://akakom.org/~andec/tutor/repo-dvd_files/Screenshot-Copy%2520Disc.png[/IMG]
choose file image from menu copy disc to: and after that, click write button.
then save the file on preferred partition that your prepare for the repos ISO image.
Repeat this step to another 4 DVD + the installer CD.
[IMG]http://akakom.org/~andec/tutor/repo-dvd_files/Screenshot-Copying%2520Disc%2520to%2520a%2520Disc%2520Image.png[/IMG]


Before continue to next step, you need to remove the Internet Update setting on your Software Package Manager.
[IMG]http://akakom.org/~andec/tutor/repo-dvd_files/Screenshot-Software%2520Sources.png[/IMG]
Just remove all checked on the check-box.

3. After finish copying all 5 DVD and 1 installer CD to your Harddisk.Now, we will try to install one application that we will use to handle the ISO file and act like "virtual drive" for the DVD ISO file. Its name Gmount. All you need to do is, mount the ISO file to cdrom default mounting-folder (in this case /cdrom/). open your Terminal then sudo to root account.mount the ISO file to your /cdrom/ with this command. (remember, run this command with root access)
#mount {your ISO file path address} /cdrom/ -o loop
in my place it would be:

#mount /gudang/Ubuntu_Repository/Ubuntu_7.10_-_i386_-_DVD_1_of_5.iso /cdrom/ -o loop

Now, open Add and Remove application, then find Gmount application. Remember to choose All available application on Show menu.
[IMG]http://akakom.org/~andec/tutor/repo-dvd_files/Screenshot-Add-Remove%2520Applications.png[/IMG]

{pic deleted}

after found the application click Apply icon, then it will install the application on your Ubuntu system. If it got failed like this:
{pic deleted, limited 8 pic, sorry}
then repeat the mount command upside.

After finish the installation , you will found a massage box :
{pic deleted}
Then your ready to use the application.

4. For example, we will try to install bluefish application. First, open Add and Remove application. The find bluefish after that try to install it. Now you will found a message box that tell you the repo DVD not on it place (/cdrom), now run the Gmount application
[IMG]http://akakom.org/~andec/tutor/repo-dvd_files/Screenshot-Gmount-iso.png[/IMG]

Then open your ISO file, just click the Open button, and direct it to your ISO file.
then on Mount Point text box just type /cdrom/.
Next click Mount button.
Back to the message box click Ok button.
And.. you will find the the application continue installed. repeat this step if the application request for another DVD disc, just change the ISO file with the same DVD number that it request.

Happy installing!


Mada R Perdhana
Informatics Engineering
Informatics & Computer Academy STMIK AKAKOM Jogjakarta, Indonesia
[www.akakom.ac.id](www.akakom.ac.id)
[email]mada@akakom.org[/email]

---

