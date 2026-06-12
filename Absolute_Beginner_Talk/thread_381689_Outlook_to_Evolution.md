---
title: "Outlook to Evolution"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by joellord on 2007-03-11
Hi everyone,
  thanks to the numerous posts here, I managed to get everything to work on my laptop.  Ubuntu is great so I installed it over my Windows partition.  Now, I just realized that I need Windows to read my PST file to migrate it.  Is there any way to read my PST file (from OL 2007) without reinstalling Windows ?  I tried ReadPST but it didn't work for this version of OL.

Thanks for the help,
Joe

---

### Post by HereInOz on 2007-03-11
Check this one out:

[http://outport.sourceforge.net/](http://outport.sourceforge.net/)

It claims to be able to do the job, but I have not used it myself.

---

### Post by joellord on 2007-03-11
Unfortunately, outport is a win32 app.  I need something I can run under Ubuntu.  Any other alternatives ?

Joe

---

### Post by mozkaynak on 2007-03-11
you can install wine to run a win32 application.
[www.winehq.com/site/download-deb](www.winehq.com/site/download-deb)

---

### Post by jazzman83 on 2007-03-12
I used outport to get all of my outlook emails but now they cannot be imported properly into Evolution.  

All my messages are in either .html or .txt format and easily viewable but for the life of me I cannot add them to my Evolution mail.  When I do try and use the import function, it always adds them to my contact lists and then I have the pain of erasing it all.

Any help would be great.

---

### Post by joellord on 2007-03-12
How did you get outport to work ?  When I try 

wine outport

I get the following result:

err:module:import_dll Library MSVCIRT.dll (which is needed by L"Z:\\home\\joel\\outport\\libdb31.dll") not found
err:module:import_dll Library libdb31.dll (which is needed by L"Z:\\home\\joel\\outport\\outport.exe") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\joel\\outport\\outport.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\joel\\outport\\outport.exe" failed, status c0000135

---

### Post by nutz on 2007-06-03
I am looking for somthing like this as well for a few O2K3 PST files...

---

### Post by terlmann on 2007-07-25
same issue. outport doesnt work.

---

### Post by juanbretti on 2007-07-31
**joellord**, I will try ReadPST. Thanks for that information: I'd no idea about that software.

---

### Post by hartdg on 2007-08-12
joellord: I think the easiest route for you is as follows:

0. Find a friend who has Windows and MS-Outlook running on a PC who's prepared to let you use the PC for a couple of hours (& install Thunderbird on it). The PC should have enough free space to accommodate double the size of your .pst files and the Thunderbird installation.

1. Take a copy of the MS-Outlook .pst files on to a friend's PC. 

2. Create a new profile in Outlook and open your .pst files in that profile. For the duration of the operation make the profile the default profile in Outlook. To create a profile (right-mouse on the MS-Outlook icon in the menu system and select "Properties". Then select "Show Profiles". Check the "Prompt for profile to be used" button. Click "Add" .... (I assume that you know how to add  .pst files into Outlook, if not, I can help).

3. Make sure that none of your .pst files have e-mails in the top level of the file. If there are some then move them into a sub-folder (otherwise Thunderbird will miss them). When this is done, close Outlook.

4. Install Thunderbird. It will then offer to import address book & e-mails from Outlook. Depending on the size of your .pst files this could take some time (several hours). 

5. When it's done Thunderbird will have created a set of subdirectories in the path "Documents and Settings/<user>./Application Data/Thunderbird/Profiles/<profile code>/Mail/Local Folders" (or something similar)

6. Copy all the .sbd folders that are in /Local folders (there should be one for each of your .pst files) into the folder "/home/<user>/.evolution/mail/local" on your Linux system
(see post 13 by muguwmp67 in [http://ubuntuforums.org/showthread.php?p=3178111#post3178111](http://ubuntuforums.org/showthread.php?p=3178111#post3178111) for this brilliant tip):guitar:

If you can not see the .evolution folder in /home then select "Show hidden folders" in the View menu of Nautilus (or whatever file manager you are using).

7. Start Evolution. Next to your Inbox and other folders you should now see a folder for each .pst  As you browse through them there will be a short delay (depending on folder size) as Evolution updates its indices.

8. I migrated my Outlook Contacts via File / Import & Export in MS-Outlook to "Tab delimited (Windows)" files and then imported these files into Evolution via File / Import / Import single file for each contacts folder/file. 
Thunderbird appears to store the info it adds to address books (from Contacts) higher up the path described in pt 5 (in the <profile code> sub-directory). You could try copying the *.mab files to Evolution and seeing what it does with them but the approach I used is quick and easy (unless you have dozens of different address books).

9. Clean up your files from your friend's PC and uninstall Thunderbird (unless he wants to keep it). Delete the profile you created in Outlook and restore his default profile.

10. I've not discussed migrating Tasks, Notes or Calendar items here. You'll need to look elsewhere for support on that if required.

Dave

---

