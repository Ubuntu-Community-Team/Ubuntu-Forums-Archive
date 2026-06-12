---
title: "Restoring a home directory with File Roller"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by RogerD on 2007-02-20
Hi

I've been dutifully creating a back-up tar file of my home directory with File Roller. I'll shortly be getting a new computer, and I want to use this tar file to create a copy of my exiting home directory on the new computer. The trouble is, I can't see how I'm going to do this.

I've been doing some experiments, and while I can open/extract the tar file,  getting the files where I want them is proving a real problem.

If I extract on the external hard disk, I can create my home folder, naturally called roger, but my system won't let me copy  this into the home directory on my internal hard disk - it tells me I haven't permission. I can copy the folder into roger, but then I'm one level too far down the file hierarchy, if you see what I mean.

File roller is really a nice utility, and I suspect I'm doing something really silly.

Anybody any ideas please?

Roger D

---

### Post by Tomosaur on 2007-02-20
You will need to 'sudo-up' to do something like this, but you're making life difficult for yourself. The best method is to create an archive of everything **inside** your home folder, rather than one of your home folder itself. Your new machine will need to be set up, and you're going to need to create your user again - which will automatically create a /home/roger folder. This way - you can just extract everything into your new home directory, and everything will be hunky dory :)

If you want to go ahead and do what you've been trying to do, you need to start file roller using gksudo. I can't remember what the actual command for file roller is, so I'll just call it file-roller. To start with root permissions, press F2, then type:
```

gksudo file-roller

```

The password it will ask for is your own, and then you should be able to extract into the /home folder.

Again - you should probably rethink how you're doing this. It's best to just archive everything **inside** the /home/roger folder than to archive the folder itself.

---

### Post by RogerD on 2007-02-20
Many thanks for the response. I suspect this is going to sound a bit dumb, but how do I create an archive of everything inside my home folder - including all the hidden files?

---

### Post by Tomosaur on 2007-02-20
Open up your file browser (I assume you're using Ubuntu? If so, click Places, then Home Folder), hit ctrl+h, then ctrl+a, then right click on one of the files and select 'create archive'. :)

---

### Post by RogerD on 2007-02-20
Yes, I'm using Ubuntu.

I'm trying this out in the home folder of a user called, natrually, 'test'.

I've selected all the files in test, using ctrl+h and ctrl+a, and created an archive, which takes the name of test.tar on my external hard disk.

I've copied this file back into the opend home directory of test, and selected extract here. This creates a file called test.tar_FILES, and when extraction is complete, I find test.tar inside this folder.

Clearly, I'm still doing something wrong.

---

### Post by Tomosaur on 2007-02-20
Well that is odd behaviour. Through the GUI, the end result should be test.tar_FILES - that's ok, but the contents of that should be whatever was in the test folder. Here's the step by step guide.

Click Places, then Home Folder
Press Ctrl+h. This will display hidden files.
Press Ctrl+a. This selects all files in this directory.
Right click on one file, and select 'Create Archive'
Name your archive, and select which archive format you wish to use.
Put the archive wherever you want to extract it (For example, the Desktop)
Right click the archive file.
Select 'Extract Here'
This should create a folder called my_file.extension_FILES (for example, test.tar_FILES)
Enter this folder, you should see the files you initially selected using ctrl+a.

---

### Post by RogerD on 2007-02-20
Still something very funny going on here

I select all the files in the 'test' home folder, creating an archive test_archive.tar in my external hard disk.

I perform 'extract here' on this folder, creating a new folder 'test_archive.tar_FILES'

I enter this folder, and, sure enough, I see all the files originally in the test home folder.

I select all these files, right click on one and select copy

I do a paste in the test home folder, selecting the 'replace all' option.

This re-creates my test home folder, so I seem to be home and dry. Unfortunately, nothing now works. If I click on the home folder icon in the panel,  the home folder doesn't open, and if I click on the Firefox icon, that doesn't open either.

I must still be doing something wrong.

---

### Post by Tomosaur on 2007-02-20
Do you get any errors, or is it that nothing happens at all?

---

### Post by RogerD on 2007-02-21
No, no errors.

What I've found is that if I log out, then log on again as test, things start working. I can start the home folder from Places, and Firefox starts up, athough the default home page has reverted to Ubuntu, rather than Google.

I wish I understood what was going on, I'm not very confident that this is a good way of copying home folders between computers. I'm particularly keen that all my evolution files, especially my address book, will copy successfully.

---

### Post by Tomosaur on 2007-02-21
There may be something going wrong with permissions here. Open up a terminal, and type:
```

ls -l ~

```

That wil give you the permissions of your own home folder. Paste the output here please.

Then, use this command:
```

ls -l /home/test

```

And paste the output up here. Do all of this from **your** user please.

---

### Post by RogerD on 2007-02-21
> **Tomosaur said:**
> There may be something going wrong with permissions here. Open up a terminal, and type:
```

ls -l ~

```

That wil give you the permissions of your own home folder. Paste the output here please.

Here's what I get:

lrwxrwxrwx  1 roger roger      26 2006-06-09 14:48 Examples -> /usr/share/example-content
drwxr-xr-x  3 roger roger      80 2007-02-15 09:39 gracie_fileds
drwxr-xr-x  2 roger roger     136 2007-02-14 17:43 House move
-rw-r--r--  1 roger roger   62976 2006-11-19 17:32 Invoice.doc
drwxr-xr-x  2 roger roger     216 2006-11-24 15:34 Letters
drwxr-xr-x  5 roger roger    3472 2006-06-24 20:18 linuxcommand.org
drwxr-xr-x  2 roger roger     128 2007-02-14 09:00 Money
drwxr-xr-x  2 roger roger     128 2007-02-08 20:22 mortgage
drwxr-xr-x  2 roger roger     104 2007-02-17 14:00 new_pc
drwxr-xrwx 22 roger roger     696 2007-01-06 18:02 Pictures
-rw-r--r--  1 roger roger     483 2007-01-06 19:25 plugin_stack.trace
drwx------  2 roger roger     296 2006-06-09 14:29 Portfolio of articles
drwx------  2 roger roger     280 2006-06-23 16:37 Sarah's files
-rw-r--r--  1 roger roger     597 2007-01-11 19:45 Shields,_Andrew.vcf
drwxr-xr-x  2 roger roger     880 2006-10-04 20:02 Shredder order_files
drwxr-xr-x  4 roger roger     304 2007-01-27 14:58 SoftMaker
drwxr-xr-x  3 roger roger     552 2007-02-02 19:23 temp
drwxr-xr-x  2 roger roger      48 2006-10-25 08:23 Test
drwxr-xr-x  2 root  root       48 2006-11-18 17:26 Type name of new folder
drwxr-xr-x  7 roger roger     208 2006-10-08 18:54 Webpage
drwx------  6 roger roger     176 2007-02-20 12:05 Work
-rwx------  1 roger roger 3768320 2007-02-19 16:47 Work.tar
roger@roger-desktop:~$



Then, use this command:
```

ls -l /home/test

```

Here's what I get:

total 1
drwxr-xr-x 2 test test  48 2006-10-17 14:30 Desktop
drwx------ 3 test test 808 2007-02-20 20:18 Examples
drwx------ 2 test test 128 2007-02-20 20:18 Money

And paste the output up here. Do all of this from **your** user please.

Hope this all means something

---

### Post by Tomosaur on 2007-02-21
Ok, well the home folder of test seems to have the necessary permissions, but it may not be the case for the contents of the /home/test/Desktop folder. Did you extract the archive into the test folder using your login, or did you log in to the test user and extract the archive that way? You should have done the latter - otherwise permissions are pretty much guaranteed to be screwed up. It really is just a matter of doing it in the right order - there's absolutely no reason why this shouldn't be working. The only problems would be user-specific files (say, if you had a file in your old home folder which depended on being in that exact folder, or whatever), but those problems can be overcome later on. The act of moving the contents of the home dir really is just a case of moving the files - it shouldn't be this complicated.

That being said - I though you were trying to copy your home folder onto a new machine? From the output you pasted above - it's pretty obvious that you've done something else here, otherwise the contents would be identical, aside from the permissions. It's kind of hard to diagnose your problem because of this. You should test what you're actually trying to implement:

1) Create an archive of everything in your home folder.
2) Log out
3) Log in to the test user.
4) Copy the archive from /home/roger to /home/test
5) Extract the archive, choosing to overwrite the files.

Most of the files should then work. There's no reason why they shouldn't. SOME files, which  absolutely rely on being on your home folder (/home/roger), may encounter problems, but these can be fixed. Things like desktop shortcuts however, should work fine.

---

### Post by Zafrusteria on 2007-02-21
Hi

From your original post you have an archive file of your home directory and you want to move this to another installation of Linux but can only restore it to your home directory in the new installation. I assume you are ending up with something like :

/home/roger/roger

If that is the case why not do that and then move the file up one level :-)

cd ~                (takes you to /home/roger)
cd roger          (puts you into /home/roger/roger)
mv * ..             (moves all files and directories sub-dirs as well UP-one level)
cd ..                 
rmdir roger    (now getr rid of the now empty roder directory)

Job done.

Now change your archive to backup the contents of /home/roger  and not the home roger directory and its contents.

Hope that helps.

---

### Post by RogerD on 2007-02-22
Thanks for all your help on this everybody.

I'm afraid the moving the folder up a level idea didn't work. I couldn't overwrite folders one level up, and then my test folder wasn't empty. However, I'm reasonably confident I'll be able to get most of my home folder copied across with file roller, and if it takes a while to work, there's always my old machine to work on.

I'm told there's a good GUI-based archiving tool in 6.10, but, for the present, I'll stick to what I know.

Regards

Roger D

---

