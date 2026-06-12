---
title: "Security delete files"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by unknown user on 2008-01-03
**[COLOR="Green"]How can you totally delete programs from Ubuntu like in windows the security programs?[/COLOR]**

---

### Post by ~LoKe on 2008-01-03
Ubuntu has add/remove in system -> administration or system -> preferences.  Or, in the terminal:
```
sudo dpkg -r packagename
```

---

### Post by unknown user on 2008-01-03
Does this delete the whole of the system or does it only delete individual files in the rubbish bin?

---

### Post by LaRoza on 2008-01-03
what do you want to do? Uninstall programs, or delete files?

---

### Post by shad0w_walker on 2008-01-03
Your posts are very unclear and talking about different things each time. Make it clear what you want to do. You started off talking about uninstalling programs and now your talking about something to do with either the whole system or the trash folder. Make your mind up, tell us what you want to do and we can actually help.

---

### Post by ~LoKe on 2008-01-03
> **shad0w_walker said:**
> Your posts are very unclear and talking about different things each time. Make it clear what you want to do. You started off talking about uninstalling programs and now your talking about something to do with either the whole system or the trash folder. Make your mind up, tell us what you want to do and we can actually help.

I thought I was just confused so I opted to let someone else handle it.  But apparently we're on the same page.  :lolflag:

---

### Post by unknown user on 2008-01-03
I see your point.  What I want to do it totally delete a file that I have got in my Deleted Items Folder.  In windows you can use a program that totally deletes files called Cyberscrub which I always use.

---

### Post by llamakc on 2008-01-03
> **unknown user said:**
> I see your point.  What I want to do it totally delete a file that I have got in my Deleted Items Folder.  In windows you can use a program that totally deletes files called Cyberscrub which I always use.

```

secure-delete - tools to wipe files, free disk space, swap and memory

```

Secure Delete is available in the repositories. Open Synaptic and search for "secure delete". Install it. Read the documentation on it too.

---

### Post by unknown user on 2008-01-04
[COLOR="Green"][B]Thanks for this.  I have done what you suggested (Open Synaptic and search for "secure delete". Install it) and it looked like it installed all OK, so I then rebooted.  However, now I can not see it in the Applications (or any of the) dropdown lists or when I right click on the file that I want to Secure Delete which is in my Trash folder I do not see the Secure Delete option.  Am I using this Secure Delete program wrong and if so how do I use it?  Also where can I find the documentation that you mentioned?

In the windows Cyberscrub program that I previously mentioned, you have the option to set the deleting method (from weak x2 pass all the way through to Strong x32 pass).  Do you get this option within this Secure Delete program and if so how do I set it?[/B][/COLOR]

---

### Post by perixx on 2008-01-04
hi unknown,

secure-delete is a set of CLI (command line interface) tools, no GUI is provided... perhaps someone wrote a good frontend for it.

just been downloading it myself; the documentation can be found in > /usr/share/doc/secure-delete though I find it irritating that 'man secure-delete' of 'info secure-delete' isn't linked to the info there.
You can, however get some basic info by just typing 
```
[tool] --help
``` in a terminal.
The four tools secure-delete consists of are:
> /usr/bin/srm
/usr/bin/sfill
/usr/bin/sswap
/usr/bin/smem

perixx

---

### Post by unknown user on 2008-01-04
Cheers, for this, but when you say "in a terminal.  The four tools secure-delete consists of are:" what do you mean?:confused:

---

### Post by seventhc on 2008-01-04
It's all in the documentation that was mentioned earlier. I think you would understand it more if you read it. :)

---

### Post by perixx on 2008-01-04
'secure-delete' is only the package's name, the tools are the four single CLI-applications... 

You can make use of them either by typing a command in a terminal, along with the desired options (refer to [application] --help first) and target file(s)/folder(s), which is rather dreadful unless you just have some rare use for it with single folders or the likes.

The smarter way would be to write scripts and execute the commands with them - for pre-defined actions, which can be as simple as a button pointing to a little script pointing to the desired app, doing always the same step, like deleting the securely deleting the trashbin (havent looked into that by now).

The most convenient way, of course, is using a good graphical frontend (or GUI), which passes predefined actions to the CLI-applications... I really have to look for a good frontend for them :]

perixx

---

### Post by unknown user on 2008-01-05
Hi there, Cheers for this, but I am having such a game with this it is unreal.  You hear all the stories about things not being deleted when you think they are such as financial data and such like, all I need to do is make sure that when I delete something it is gone.
I am going tp have a look around for something that has a GUI front end as I am still new here and command lines are still a bit of a grey area to me.
If anyone knows of any other secureity delete programs for Ubuntu, please let me know.

---

### Post by perixx on 2008-01-05
the README file in the docs of 'secure-delete' provide some interesting aspects to consider, concerning this matter (bad clusters and such) - there's even a test method described if the program provides really secure deleting on your system - it's well worth reading it!

perixx

---

### Post by unknown user on 2008-01-06
[COLOR="SeaGreen"]I have had a look at the readme and it sure is interesting reading.  So from what I can see and I am sure I am wrong, is this the line that I would need to run in the command line?
[I][B]
 srm -d QuickTimeInstaller.exe[/B][/I]

From what the file says below?

When I do run this line this is what I get - 

[B][I][COLOR="RoyalBlue"]unknown@unknown-laptop:~$  srm -d QuickTimeInstaller.exe
Error: File QuickTimeInstaller.exe - No such file or directory
unknown@unknown-laptop:~$  srm -d Deleted Items QuickTimeInstaller.exe
Error: File Deleted - No such file or directory
Error: File Items - No such file or directory
Error: File QuickTimeInstaller.exe - No such file or directory
unknown@unknown-laptop:~$ [/COLOR][/I][/B]


3. COMMANDLINE OPTIONS

     Here are the commandline options:

     srm    [-d] [-f] [-l] [-l] [-v] [-z] file [file] [another file] [etc.]
     sfill  [-i] [-I] [-f] [-l] [-l] [-v] [-z] target-directory
     sswap  [-f] [-l] [-l] [-v] [-z] /dev/of_swap_filesystem
     smem   [-f] [-l] [-l] [-v]

     The -s options are depricated now, and will be ignored.

      -d   don't delete the dot special files "." and ".." on the
           commandline (only srm)
      -i   wipe only free inode space, not free disk space on the filesystem
           (only sfill)
      -I   wipe only free disk space, not free inode space on the filesystem
           (only sfill)
      -f   fast writes without O_SYNC and sync() between writes. Much faster
           but less secure.
      -l   lessens the security. Only one random plus one pass with 0xff are
	   written.
      -l   a seconds time as parameter switches into the insecurest mode,
	   it overwrites the file only once with 0xff.
      -v   turn verbose mode on.
      -z   last wipe mode writes zeros instead of random data
     file  file to delete. Wildcards are of course allowed.
           For unix: you need write permissions. For msdos: It may be hidden,
           system, readonly etc. we don't care.
    target-directory  target is a directory in the filesystem to write to.
    swap_filesystem   your swap filesystem. Unmount it first!!
                      only tested on linux

     Options may be applied like "-lfv", "-l -f -v" or a mix.

[/COLOR]

---

### Post by seventhc on 2008-01-06
if you do ls from the terminal do you see [COLOR=SeaGreen][B][I][COLOR=RoyalBlue]QuickTimeInstaller.exe
[/COLOR][/I][/B][COLOR=RoyalBlue][COLOR=Black]if not, you will probably have to cd to the directory that it is in or provide the path to it.[/COLOR]
[/COLOR][/COLOR]

---

### Post by unknown user on 2008-01-06
How do I do this as I have not got a clue.  The deleted item is trash.  Can you give me an idea of how to write the line.

---

### Post by llamakc on 2008-01-06
Type the letter l and the letter s. Lowercase:

```

ls

```

Looks like You created a directory with a space in the name, and that's where the file you want deleted is. change directory to that place with

```

cd /path/

```

In this case, type the command "cd" (w/o the quotes) and then BEGIN typing the name of the directory. After you've typed a letter or two, hit your tab key. Voila! Tab completion rocks.

Otherwise you will have to wrap that directory with the space in the name INSIDE of quote marks, or escape the space by using the \ backslash.

---

### Post by unknown user on 2008-01-06
My mental block is not going here:

unknown@unknown-laptop:~$ cd/trash
bash: cd/trash: No such file or directory
unknown@unknown-laptop:~$  srm -d cd/trash/QuickTimeInstaller.exe
Error: File cd/trash/QuickTimeInstaller.exe - No such file or directory
unknown@unknown-laptop:~$ Is
bash: Is: command not found
unknown@unknown-laptop:~$

---

### Post by scorp123 on 2008-01-06
> **unknown user said:**
> cd/trash Space matters. "cd/trash" is not a valid command. Besides, there is no such location with the name "/trash". What you probably meant is ".Trash" inside your home directory? So the command would be ```
cd .Trash
``` ... And please mind the spaces. Space matters.

---

### Post by perixx on 2008-01-09
Scorp123, I guess you're speaking of /home/.Trash-0? 
```
ls -la
``` showed it on the CLI.
I'm curious how one could manually access via it / delete content from there without changing the ownership or adding a the group and permission for 'USER' first? 

I changed the owner to USER as a test with ```
sudo chown USER .Trash-0
```and there were 2 other folders in .Trash-0, which both needed the same procedure to become accessible. There was the same content in it (some old deleted files).... I changed back everything to original status, then.

But I can't quite figure how one might use 'srm' to do all of that automatically - or maybe there's a different way to do it?

perixx

---

### Post by scorp123 on 2008-01-09
> **perixx said:**
> Scorp123, I guess you're speaking of /home/.Trash-0? I have like 8 systems here, and on all of them it's **.Trash**   .... not ".Trash-0" or anything like that.

---

### Post by mc4man on 2008-01-09
myself i just use shred running from the r.click menu. while it's probably not as effective as secure-delete it's easy to setup and use
[http://ubuntuforums.org/showthread.php?t=531703&highlight=shred](http://ubuntuforums.org/showthread.php?t=531703&highlight=shred)
would be interesting to see if one could setup a secure-delete command in nautilus-actions 
............. if whomever is having such trouble creating path to .trash then why not just move the files to somewhere else like the Desktop.

---

### Post by scorp123 on 2008-01-09
> **mc4man said:**
>  would be interesting to see if one could setup a secure-delete command in nautilus-actions  You mean something like this?
[http://my.opera.com/qwertsad/blog/2007/07/12/nautilus-script-shredder](http://my.opera.com/qwertsad/blog/2007/07/12/nautilus-script-shredder)
[http://my.opera.com/qwertsad/blog/2007/07/12/nautilus-script-secure-remove](http://my.opera.com/qwertsad/blog/2007/07/12/nautilus-script-secure-remove)

> **mc4man said:**
>  ............. if whomever is having such trouble creating path to .trash then why not just move the files to somewhere else like the Desktop.  Yeah, exactly.

---

### Post by unknown user on 2008-01-10
[COLOR="Navy"][B]mc4man, I have had a little look at your post and I too would like to use something nice and easy to delete the files.  Secure Delete just seems too much hard work.  I will have a look at your link tonight and see if I can set it all up. 
Will also try the other links and points also listed and post the results.
Cheers, guys [/B][/COLOR]

---

### Post by hyper_ch on 2008-01-10
Well, another approach of would be that you encrypt your filesystem completely... then you want have to worry about secure deleting individual files - as long as the encryption key isn't leaked...

---

### Post by Paqman on 2008-01-10
On a related note: if you want to securely clean up all the free space on your drive you can use the [scrub](http://www.ubuntugeek.com/securly-clear-free-hard-drive-space-with-disk-scrub-utility.html) utility.

---

### Post by unknown user on 2008-01-10
[B][COLOR="Navy"]Paqman, if I deleted a file the normal way, would that them remove the link as in Windows, so place it in the 'free space' area ready for when I needed to use that space?
If this is the case would it be OK to delete tthe file then use this free space cleaner that you posted the link to. to ensure that it was totally deleted so that it can not be recovered?[/COLOR][/B]

---

### Post by Paqman on 2008-01-10
No, but if you deleted it from the trash and then ran scrub it would be completely gone.

That's overkill for just deleting a single file though. Scrub is designed for cleaning whole directories or drives.

---

### Post by 3rdalbum on 2008-01-10
I second the idea of encrypting the entire filesystem or the entire home directory. If the data you've deleted is so important that you don't want a dedicated person to get at it, do you really want them looking at the things you haven't deleted? 

Unless you have an encrypted filesystem, anybody with physical access to your computer can basically boot up a live CD and view the entire contents of your hard disk - you don't even need to be a dedicated person with time, money, resources and experience to get at your data that way.

Since you are obviously completely new to Linux and the command-line, I probably wouldn't recommend you set up an encrypted filesystem on your main computer just yet. There is potential for data loss when setting it up if you don't know what's going on. But you can always try it in a virtual machine or on a spare computer to gain the experience.

With an encrypted filesystem, not only will nobody be able to get at your undeleted data without your password, but they'll even be completely stopped from getting to deleted data too.

---

### Post by gentracer on 2008-06-18
I ran sfill on my ext3 drive last night to wipe the free space.  The drive started out with 74% used space.  This morning, I had the error:

File size limit exceeded (core dumped)

Now my disk shows 97% used - ugh!

How do I clear out whatever is using that 23% of my space?  I was running as root.  I have searched for a core dump file and have looked in the /tmp directory to no avail.  I have not rebooted yet - would that help?

Any help would be appreciated.

Thanks in advance--

---

### Post by seventhc on 2008-06-18
I've never gotten that error, but I did stop it running once and the memory was almost full like yours, a reboot cleared it up and brought it back to its original size.
That will probably fix it.
I hope it does. :)

---

### Post by locosmurf on 2008-06-18
hey guys,

instead of going through all this trouble to delete something, wouldn't it be easier to "cd" to the directory and use "rm"? or even "shift delete"? what is the advantage of using 'secure-delete'?

---

### Post by hyper_ch on 2008-06-18
(1) you use a journaled system
(2) only TOC entry will be deleted
(3) if the actual deleted data will not be overwritten (multiple times) it can be restored

---

### Post by scorp123 on 2008-06-18
> **locosmurf said:**
>  instead of going through all this trouble to delete something, wouldn't it be easier to "cd" to the directory and use "rm"? or even "shift delete"?  Sure, if you don't mind that others are then able to restore again what you tried to hide by deleting ...

> **locosmurf said:**
>  what is the advantage of using 'secure-delete'?  It's secure ... as the name suggests? :)

For some odd silly reason people believe that when they delete a file that it's gone and that whatever was in that file can't come back to haunt them or harm them in any way.... And this is simply not true!

And you don't even have to be working for law enforcement agencies in order to be able to do that ... Anyone able and willing to read a few "man" (= manual) pages and who knows his ways around things such as the "dd" tool might be able to retrieve deleted files if they invest enough effort and energy.

---

### Post by gentracer on 2008-06-18
> **seventhc said:**
> I've never gotten that error, but I did stop it running once and the memory was almost full like yours, a reboot cleared it up and brought it back to its original size.
That will probably fix it.
I hope it does. :)

Unfortunately, a reboot did not help.  I have to think that there are temporary files out there somewhere, but finding them and deleting them is eluding me.  If the program had completed successfully, it should have removed all the files it created, but since it didn't, I don't know where to look. :confused:

Anyone have any ideas??

By the way, to answer another question - this system is used for work and I have very sensitive client files which need to be fully removed.  Unfortunately, I know that I've just deleted some files (not using shred or srm), so free space needed to be wiped.

---

### Post by gentracer on 2008-06-18
Ah - found it.  Really not hidden at all - after the reboot there was a very large file in the / directory.

---

