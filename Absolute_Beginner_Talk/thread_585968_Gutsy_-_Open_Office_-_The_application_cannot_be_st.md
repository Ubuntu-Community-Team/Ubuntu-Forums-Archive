---
title: "Gutsy - Open Office - The application cannot be started"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-21
Is Gutsy buggy?

When I try to start Open Office Word or Spreadsheet  I get an error:

"The application cannot be started"

Carl

---

### Post by jflaker on 2007-10-21
I have had this once or twice.....through Synaptice Package Manager, COMPLETELY uninstall the applications and reinstall it.  It should pull a fresh copy and install it.

Good luck

---

### Post by cwmoser on 2007-10-22
I completely removed all openoffice and then reinstalled -- still get the message:

OpenOffice.org 2.3
The application cannot be started.

Does openoffice write to an error log that I can check?

Carl

---

### Post by Paul820 on 2007-10-22
Run it from the terminal and any error messages you get will show up there.
Type:
> ooffice -writer
Or whichever one you are using.

---

### Post by cwmoser on 2007-10-22
This is what I get:

$ openoffice -writer
[Java framework] Error in function createSettingsDocument (elements.cxx).javaldx failed! 
[Java framework] Error in function createSettingsDocument (elements.cxx).
** (process:6138): WARNING **: Unknown error forking main binary / abnormal early exit ...

$

.. whatever that means.  Must be something to do with Java.

Any suggestions?

Carl

---

### Post by Maestro23 on 2007-10-22
> **cwmoser said:**
> This is what I get:

$ openoffice -writer
[Java framework] Error in function createSettingsDocument (elements.cxx).javaldx failed! 
[Java framework] Error in function createSettingsDocument (elements.cxx).
** (process:6138): WARNING **: Unknown error forking main binary / abnormal early exit ...

$

.. whatever that means.  Must be something to do with Java.

Any suggestions?

Carl

Similar problem to yours.  Check this thread: [http://ubuntuforums.org/showthread.php?t=572821](http://ubuntuforums.org/showthread.php?t=572821)

---

### Post by cwmoser on 2007-10-22
I tried this:

(1) ctrl-alt-backspace to restart X and GDM. Then tried running Writer before doing anything else. This didn't help me at all. Writer still would not start.

(2) Using synaptic I reinstalled the following: openoffice.org, openoffice-core, openoffice-gnome, openoffice-gtk, openoffice-base, openoffice-calc, openoffice-draw, openoffice-writer, openoffice-impress, openoffice-common.

.... still same error.

Carl

---

### Post by cwmoser on 2007-10-22
Could this be a hint - I can start openoffice like this:

sudo openoffice -writer

Unless I start as root, openoffice will not run.

Carl

---

### Post by cwmoser on 2007-10-22
OK, I found the solution.  What happened was that some permissions got screwed up in the hidden directory (.openoffice,org2) in my home directory.

I just created a new user account and deleted my old one.

Carl

---

### Post by beanco on 2007-10-23
i am having similar problems,

how does deleting one account and creating a new one help?

thanks

robi

---

### Post by cwmoser on 2007-10-23
> **beanco said:**
> i am having similar problems,

how does deleting one account and creating a new one help?

thanks

robi


Robi, I had tried to "upgrade" my Feisty Fawn version of Ubuntu and it did not go well.  
So, I gave up and created a new instance of Gutsy Gibbon in another partition.
Then, I copied all my files from the home directory from the upgrade attempt.  

Searching for an answer to this problem, I noted that some owner and group permissions were not exactly kosher.  I tried to manually fix these permissions but it did not work out and then I got the bright idea to delete the account and then recreate the account.

Carl

---

### Post by beanco on 2007-10-24
Carl,

that is sg worth considering.

thanks for the info!

robi

---

### Post by msisk on 2007-10-29
Just as a possible workaround for those who don't want to delete their account, I had success using synaptic to completely remove all of the openoffice packages.  Then manually deleting my home/.openoffice.org2 directory.  And then reinstalling openoffice.

---

### Post by woutertje on 2007-11-04
Even better,
Open a terminal and type: "sudo chown -R [your-username] .openoffice.org2"
and you're done!

---

### Post by crowndip on 2007-12-15
Or you can delete your openoffice configuration in your home directory.

Delete the directory .openoffice.org2 in your /home

Then when you start openoffice, it will recreated the directory itself.

---

### Post by beanco on 2007-12-16
crowndip

I did this

```
Delete the directory .openoffice.org2 in your /home
```

and got this

```
 rm: cannot remove `.openoffice.org2': Is a directory
```

Sure it is just because I am a n00b, but what have I done wrong?


Robi

---

### Post by The Cog on 2007-12-16
You don't say how you tried to delete the directory. rm won't work because its a directory not a file. this will work of the ownershi[s and permissions are right:
**rm -rf .openoffice.org2**
but if the permissions are wrong you may need sudo in front:
**sudo rm -rf .openoffice.org2**
but personally, I always just rename it to start with, so if the problem still persists afterwards, I can put it back again.

---

### Post by beanco on 2007-12-16
yeah, I tried rm but that did not work, even with sudo... so I went to synaptic...

got it all off

reinstalled it and i could not get the new installation to open, just kept getting that annoying error msg and then whatver prgm I was opening would try to reopen... an endless cycle!

robi

---

### Post by The Cog on 2007-12-17
Reinstalling the application won't help if the problems are something in your personal OpenOffice settings. If you're not comfortable with the command line, use nautilus (the file explorer) to delete .openoffice.org2 from your home folder. But it's a hidden directory so you'll have to use the menu View->Show Hidden Files to be able to see it.

---

### Post by beanco on 2007-12-21
I deleted it using nautilus but was not able to reinstall it successfully.

I mean the new install of open office just gave me the same old probem



so now what?

---

### Post by uiop12 on 2007-12-23
I got the same problem, and got it solved like this:

**sudo chown -R  $USER:$USER ~/.openoffice.org2**

So no need to reinstall OpenOffice or recreate user account.
The problem was that the root owned ~/.openoffice.org2 directory.
Probably I had first time accidentally started OO as root.

---

### Post by beanco on 2007-12-23
Like I keep saying I am the n00biest of the n00b so if I were to follow your instructions uiop12   I would 
sudo chown -R $rob:$rob ~/.openoffice.org2

right?

but what happens in the case that I deleted the openoffice.org2 in nautilus?

robi

---

### Post by beanco on 2007-12-23
I answered my own question

```
chown: cannot access `/home/rob/.openoffice.org2': No such file or directory
rob@rob-desktop:~$ 


```

robi

---

### Post by cecst on 2008-03-21
The solution seems to be
  sudo chmod -R $USER .openoffice,org2

This worked for me because the owner of this subdirectory when openoffice would not start was "root", so when I started openoffice as myself the program did not have permission to write in this subdirectory. When openoffice was started with sudo, it was able to write to this subdirectory. After executing the above command, I had permission to write in this subdirectory and so did openoffice when I started it as myself.

The "-R" option changes not only the subdirectory .openoffice.org2 but also all the files and directories within it.
$USER should translate to your username. If it does not, substitute your username for "$USER".

Hope this helps.

---

### Post by prgiorgio on 2008-04-23
become root and delete the
.openonffice2 dir in your home,
then become user again
and restart the office

in other words:

cd
sudo rm -rf .openoffice.org2
exit
soffice

---

### Post by jordanharp on 2008-04-27
I just got this error in Hardy, but it's fixed. For new users, this problem is easily solved by this process:

sudo nautilus

In the File Browser that opens, navigate to /home/$User/

View hidden files by pressing Ctrl+H

Right-click on the .openoffice.org2 folder and choose Properties

Click the Permissions tab

Change the value of the Owner dropdown from root to your username

Make sure you have read and write access and that others have "Access Files" permission set on the Folder Access dropdown

Click the "Apply Permissions to Enclosed Files" button

Close the Properties dialog, and close the File Browser

OpenOffice.org should now run fine!

---

### Post by DChamp on 2008-07-01
Tried everything above, not working.
Everything OO except for Evolution email comes up and closes before showing the interface.

Any help for this ole Noob would be appreciated.

Using Hardy with all patches in a VMware Workstation window.
It's worked flawlessly until recently.
Oh, if I have an existing file and double click, programs come up fine. Only opening OO Writer, spreadsheet, presentation or database from scratch does it fail.

Thanks again for any help.

---

### Post by k4dgw on 2008-07-01
Just noticed I cannot start open office.  It does not matter whether I run it as user, or sudo.  It does not matter if I do openoffice -calc, openoffice, or soffice.

I have looked at the owner of the .openoffice.org2 directory, and it is good.  Permissions were 700, so I changed them to 755 to see if that would make any difference.  There was no change so I put it back.

I tried deleting the .openoffice.org2 directory and running again, but still no change.

From a terminal screen the following error is generated.  Open office also places a .lock file in the .openoffice.org2 directory, which I have been removing.

david@dhcppc1:~$ openoffice
/usr/lib/openoffice/program/soffice.bin: symbol lookup error: /usr/lib/openoffice/program/libtk680li.so: undefined symbol: LXAccessibleComponent14queryInterfaceERKN3com3sun4star3uno4TypeE

Dave
K4DGW

---

