---
title: "Automatic backups!"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-10-07
Back in the bad old days when I ran Windows XP, I used a lovely little program that backed up all my specified files to some server a million miles away for free.

But the program was only for windows-- is there any program I can use that uses an easy, GUI where I can back up my most treasured files? I have tried to research this before and people have talked about grvnc or something similarly titled, but I don't need just a program- Is there anything like Mozy Backup that I can use for Linux? I don't have another computer and am not going to buy one just to back stuff up on. And while I do have an ipod and a flash drive- I want more.

I hope I explained myself adequately.

thanks!

---

### Post by Pumalite on 2007-10-07
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)

---

### Post by PmDematagoda on 2007-10-07
Hey Pumalite that link doesn't work. I would like to know the answer as well as it would be useful for my "experiments":).

---

### Post by Pumalite on 2007-10-07
I know. It's not 'automatic', but is a pretty good way of doing things.

---

### Post by PmDematagoda on 2007-10-07
Pumalite I don't know if it works for you but for me, FF tells me there is 404 error with the link.

---

### Post by Pumalite on 2007-10-07
Back Up & Restore

Edited Tuesday, July 03 2007
 
This web-page is part of a larger site giving examples of how to install Windows+Ubuntu Linux operating systems 'dual boot' in a computer.  Illustrated Dual Boot HomePage

Backing up and restoring is very simple in Ubuntu, at least for me, the way I like to do it.

Page Index
1)Small Scale Back- ups and Restoring

     a. MBR backup and restore.

      b. the cp command.

2)Medium Scale Back- ups

    a. GUI method of backing up.

    b. GUI restoring general data.

   a. Firefox Bookmarks Restoring (GUI method)

   b. Evolution Restoring (GUI  method)

   c. Firefox Bookmarks Back up and restoring (Firefox Method)

   d. Evolution Back-ups, Terminal commands method.

   e. Evolution Restoring, with Terminal commands

  f. Make a backup script to run your backup commands automatically

  g. Configure 'crontab' to run your backup script regularly at the times you set

   h. Make a restore script

  i. Back-up and Restore Added Software

3) Whole Partition Back-up and Restore

   a. Complete Back-up Using File Compression

   b. GParted Partition Back-up.



Small Scale Back- ups and Restoring

MBR Backup and Restore
You can back up your MBR with a Linux Live CD such as a ubuntu 'desktop' Live/Install CD or Knoppix or similar before you begin your Linux installation.

You can use any media you like to copy the MBR backup file to and store it on. In this example I used a USB disk. You may use a floppy disk or a CD-ROM just as easily.

It isn't compulsory to name your MBR file 'OLDMBR.img', you might be better off naming it something like 09june06_MBR.img instead. I find having the date as part of the file-name can be quite handy at times when it comes time to find my old files and i need to decide which one is the one I really want to use and which ones to delete to the trash.

To USB disk:

1) Plug in USB disk cord or check to see that it is already plugged in.

2) Boot your Live CD. (Ubuntu Desktop in this example).

3) Choose Start or Install Ubuntu

4) After boot-up, USB disk icon(s) should appear on the desktop.

5) Open a terminal (Applications, Accessories, Terminal)

6) code:
     sudo dd if=/dev/hda of=/home/ubuntu/OLDMBR.img bs=446 count=1



7) quote:
   1+0 records in
   1+0 records out
   446 bytes copied,  4.3e-05 seconds, 10.4 MB/s
 
8) Open /home/ubuntu directory, locate file named OLDMBR.img

9) Open USB drive (FAT32 partition), drag and drop OLDMBR.img there somewhere.

10) Carry on with your Ubuntu Install.

Warning:

You can make a backup copy of your MBR with the entire 512 bytes, which includes the entire MBR meaning the partition table and 55 aa signature.

That may be useful for some purposes, but be sure you destroy that copy of your MBR if you decide to re-partition your disk later. If you accidentally restore your MBR backup with an out of date partition table, it will not match your new filesystems. It will cause your disk to be unreadable.  Unless it is very important data you will probably have to give it up and reformat and repartition your disk and loose all your data and have to start again.

If you only want the to make a backup copy of the bootloader code, you only need the first 466 bytes of the MBR, so it will not include the partition table. That is much safer. That is what I do, and what is shown here.
 



11) Restore command:

code:
     sudo dd if=/home/ubuntu/OLDMBR.img of=/dev/hda bs=446 count=1
Where:  ubuntu is your username (it is the default username for the live CD),
and where: OLDMBR.img is the name of your MBR backup file.

===========================================================




 
The cp Command
Every time we need to edit some important files in Ubuntu we always make sure there is a back-up copy of the file first. You will see how to use the cp command to make back-ups in all good instruction manuals and how-to's. No-one seems to bother to explain to newcomers what they need to do to actually restore the file if they need to.
 
The cp command in terminal is a very handy way to make a back-up of any file we any be working on, such as a text file.  Lets try this out on a file that isn't very important and see how it works, okay?  Now say I am working on a text file called 'myblog'. Make one yourself in your own computer and try this. Type a few lines of text into it for testing purposes if you like. I made a back-up of the file by typing this code in 'terminal' (if 'myblog' is a file located in my /home/herman directory).

code:
     cp myblog myblog_backup
 
This will make a back-up of my 'myblog' file and name it    myblog_backup.
 
The same thing should work for you too, try it.
 
Later, I make a lot of alterations to my 'myblog' file, but then I decide they are no good and I want to go back to my original story. To restore my 'myblog', I can  simply  open up a 'terminal' again, and typing the pretty much the opposite of what I typed when I made the back-up of it:

code:
     cp myblog_backup myblog     
 
This will restore my 'myblog' file to the way it was when I made the back-up. Test this out yourself with your own 'mybog' file, alter the text and then restore the original back-up copy and check to see what happens. It's actually a pretty nifty little trick. Linux is great!
    
Now, to take this a step further, you might have read the 'GRUB page' of this website, and made a back-up of GRUB's menu.lst file before editing it. The command used for that was:

code:
     sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
 
Now if we are not happy with the alterations we made to the /boot/grub/menu/lst file, we can easily restore the old one by typing the following code into our terminals:

code:
     sudo cp  /boot/grub/menu.lst_backup /boot/grub/menu.lst
 
...and that is how to perform small scale back-ups and restore jobs in Ubuntu.

 There is one possible (major) problem to be aware of when you are new to this. Imagine you followed one how-to and back up some text file like grub's menu.lst, and then modify it. Later, you follow another how-to and make a new back-up and then make more modifications to the same file. The second back-up will overwrite your first back-up so you will lose the original copy of that file. Then if you later regret something you did when you edited the file the first time you might not be able to get your computer back to its original state easily. Every user should think about this and decide what rules they want to make for themselves in regards to this type of situation. Maybe you should get in the habit of making an extra copy of the backup file and store it out of the way somewhere like in a special 'all_backups' directory you might make for yourself. Alternatively, you might make it a rule that you only make a back-up copy of the original file once, and from then on always check for the presence of a back-up file before editing the file. For example, use the 'ls' command to have a look around and see what's there first.

code:
     ls /boot/grub/     
 
If there is already a menu.lst_backup in existence we may not want to make a new one and overwrite the existing one, so we just skip that step in the how-to we are following. I suppose a really good how-to for newbies should ask the newbies to check first for the presence of an already existing back-up before giving the newbie the command to make the back-up, but it would be a lot more work for the writer to include those extra instructions every time.




===============================================================

    
 
Medium Scale Back- ups and Restoring 

 GUI Method for making backups

(a) Open your home (username) folder
(b) make a new folder and name it something like 'dec06_bkp' or something like that (dec06 being the day's date).
(c) copy or move all of your other regular folders and files into it that you want to save.
(d) make a new folder for evolution  and one for  mozilla. (Just so you can find these files again easier later on).
(e) On the 'view' menu, click 'show hidden files'.
(f) open the one called .evolution and copy whatever is in there you want, like 'calendar', 'addressbook', 'mail', 'memos' and 'tasks'. Paste all these into 'dec06_bkp', into your new evolution folder.
(g) Find the folder named .mozilla, and inside it open the one called firefox. There will be one or more directories in there with a very extraordinary name like 'ff38ksj6.default. Copy that into dec06_bkp, into your new mozilla folder.
(h) Anything else I might not have though of you want to include, go find them and copy them into dec06_bkp
(i)Move your dec06_bkp folder to your back-up media such as a CD or to another drive or another computer on your LAN.
    
GUI Method for restoring

(General data)
When it's time to restore, just find what you want in your storage media and copy it back to your home (username) folder where it came from.
In your /home/username directory, click 'View', and 'Show Hidden Files' again.

Firefox Bookmarks Restore (GUI navigation method)
For firefox bookmarks, find the mozilla folder in your backup (dec06_bkp), and in it there should be one with a funny name like xla8qen.default, or 6jef2wul.default or something like that. Inside there will be a file called bookmarks.html Copy bookmarks.html and navigate to your .mozilla folder in your home folder that you want to restore and open it. Inside .mozilla there will be a firefox directory. Inside that there will be one with a funny name like xla8qen.default, or 6jef2wul.default or something like that. Open that and paste your bookmarks.html in there. There will  be an existing 'bookmarks.html' there already. Be careful here, you might want to save a copy of your existing 'bookmarks.html' before replacing it with this newer 'bookmarks.html', which you had backed up and want to restore now.
 
Otherwise, just click 'Replace'. The new file will overwrite the old one. so you'll see a sign like the one below.
                           
fig1bkp    
                          fig 1 bkp
                                                You'll see a window similar to this.
    
Evolution Restore(GUI navigation method)
Carry out a similar procedure with your addressbook, calendar, mail, memos, and tasks. All you need to do is copy your back-up directories with the aforementioned names, and navigate to your  new .evolution directory and paste them in there, overwriting your new directories of the same name. (Presuming of course, there's nothing in them yet you'd like to save first). It's best to make sure Evolution is not running while you restore it or it will probably crash, so just close evolution before you start restoring it. Usually, your e-mail will show up right away, when you go and start evolution up on your icon for it on your top panel. Your addresses, calendar appointments and tasks might not show up until after your re-start your computer.
    
An advantage of not compressing everything into one big tar file when backing up is that you can pick and choose which items to restore at any given time a lot more easily. For your e-mail this is particularly useful. For example, it might be be good idea to make a habit of backing up our  e-mail at regular intervals. For some, once a month will do. Others, who may get lots of e-mail, such as a business, might find it necessary to back it up every day. Now it is quite often the case that you may need to find an e-mail that you remember you received some time ago.  When you have not used file compression then you can choose to restore an e-mail folder from whichever date might contain an e-mail you want to look for. For those with a huge amount of e-mail, file compression might be worth using. Consider making a lot of small tar files instead of one big one.
    
Firefox Bookmarks (Firefox Method)
Export Bookmarks File
 Start your firefox web browser. Click 'Bookmarks', then 'Manage Bookmarks', then on the 'File Menu' of the 'Bookmarks Manager' window, click 'export'. That will start the 'export wizard'. Give your file a name  that means something to you, or the day's date. Choose a folder to save it in such as /home, and click 'Save'. You can go and put it away in another folder later, such as your /home/username/backups directory.
 
Import Bookmarks File
Have the bookmarks file of your choice copied out of your backups folder or wherever you kept it and pasted out in the open in your /home/username folder ready to be imported.
Start your firefox web browser. Click 'Bookmarks', then 'Manage Bookmarks', then on the 'File Menu' of the 'Bookmarks Manager' window, click 'import'. That will start the 'import wizard'. Click 'next;, and navigate to your '/home/username' folder. Find your bookmarks file to be imported and click 'Open'.
 
I noticed that when I did this I ended up adding to the bookmarks I already had rather than replacing them. Groups of sub folders can be deleted from the right-hand pane in 'manage bookmarks' by highlighting one and holding down the 'shift key' and clicking a lower one in a group. Then right-click on the red highlighted rectangle including all folders to be deleted and click 'delete'. You can empty your bookmarks right out completely this way if you want, ready to start a brand new collection , or import a different file..
    
Evolution Back-ups, Terminal commands method
These do the same job as described above (email, addressbook, and tasks). Not recommended for firefox. It is much faster to use terminal commands for this job.
 
To make a new directory (folder) with the days date on it:
mkdir 07jan06bak
To make copies of the stuff you want to back up in it:

code:
     cp -r .evolution/addressbook 07jan06bak
     cp -r .evolution/calendar 07jan06bak
     cp -r .evolution/mail 07jan06bak
     cp -r .evolution/memos 07jan06bak     
     cp -r .evolution/tasks 07jan06bak

If you are practicing to become a real 'power' manager or secretary, these terminal commands are your best friend! They are fast!
    
Terminal commands for Restoring Evolution

code:
     cp -r  07jan06bak/addressbook .evolution
     cp -r  07jan06bak/calendar .evolution  
     cp -r 07jan06bak/mail .evolution
     cp -r 07jan06bak/memos .evolution    
     cp -r  07jan06bak/tasks .evolution
 
When you get used to the commands, you can save yourself a lot of time compared with the time it takes to do some jobs in 'GUI'. Lots of things in Ubuntu will be explained in condensed form like this. It is a little difficult to get used to at first. When you realize it is really just the same things you are used to doing in 'GUI', you will come to understand the commands quite easily. It doesn't take very long before you'll learn to understand the commands as soon as you read them. Then you'll be able to make up your own. 


Make a backup script (and a restore script) to make your backups automatically
Making a backup script
A script is a text file that has been given a name that ends with the extension .sh (short for 'shell', since they're really supposed to be called 'shell scripts', most most people just call them scripts.
A shell script contains a list of commands. They are the same as the commands you would type in a terminal normally, but this way you can run a whole list of commands in one hit.

If you type: introduction to shell scripting (or something like that) into google you will have pages and pages of helpful tutorials. My favorite one is from Rute User's Tutorial and Exposition, and the exact chapter is: 7. Shell Scripting If you want to really learn shell scripting, it would be best to refer to a proper tutorial like Rute's where everything is explained a lot better than in this page.


1. Make a directory in your /home/username folder and call it: all_backups
you could also call it any other name you like, any_backups or acer_backups, (I have a habit of making up names beginning with the letter 'a' for my most important directories and files so I can find them faster).

One requirement for shell script is shell scripts need to have #!/bin/sh at the top.
Another requirement is it has to be given file permissions that mark it as being executable.

2. Create a new empty file in the all_backups directory called: evo_bak.sh (or something similar).
gedit all_backups/evo_bak.sh
3. Open the file called evo_bak.sh and type: #!/bin/sh (in the top right-hand corner).
3 (a) type in the following commands:

rm -rf  all_backups/daily_evobkup
mkdir all_backups/daily_evobkup
cp -r .evolution/addressbook /all_backups/daily_evobkup/
cp -r .evolution/calendar /all_backups/daily_evobkup/
cp -r .evolution/mail /all_backups/daily_evobkup/
cp -r .evolution/memos /all_backups/daily_evobkup/
cp -r .evolution/tasks /all_backups/daily_evobkup/

for example,
#!/bin/sh

rm -rf all_backups/daily_evobkup
mkdir all_backups/daily_evobkup
cp -r .evolution/addressbook /all_backups/daily_evobkup/
cp -r .evolution/calendar /all_backups/daily_evobkup/
cp -r .evolution/mail /all_backups/daily_evobkup/
cp -r .evolution/memos /all_backups/daily_evobkup/
cp -r .evolution/tasks /all_backups/daily_evobkup/

3 (b) Take a look at the file permissions of the new evo_bak.sh file with: ls -l all_backups
herman@red:~$ ls -l all_backups/
total 1
-rw- - - - - - - 1 herman herman    262 2007-04-15 09:40 evo_back.sh
-rw- - - - - - - 1 herman herman    262 2007-04-15 09:38 evo_back.sh~

Okay, as we can see there are no permissions allowed yet for this script to be executed by anyone.
For the script to work it must have permission to be executed.

We can fix that with a chmod command,
herman@red:~$ chmod 0755 all_backups/evo_bak.sh
herman@testedgyeftbeta:~$ ls -l

-rwxr-xr-x 1 herman herman    262 2007-04-15 09:40 evo_back.sh
- rw- --- ---  1 herman herman    262 2007-04-15 09:38 evo_bak.sh~

Good, now our script is ready to run.

We can test our script to make sure it works by typing the path and name of the script in out terminal, like this,
herman@red:~$ all_backups/evo_bak.sh
We should see a new directory appear inside all_backups named: dailyevo_bkup
Inside that will be a backup of our evolution addressbook, calendar, mail and tasks folders.

If you want to keep (preserve) this particular backup, you must rename it. I suggest renaming it something like: 14april2007.bak (or something like that, it's a good idea to include the date in it ).
I'm just deleting mine for now, because in a few minutes I'll be making a new one to test the crontab command to make sure it works, so I'll be making another backup then too.






Use 'crontab' to make your automatic backups happen automatically.
 This method means you will be able to make an up to date backup CD-ROM very easily at any time. It is very convenient to be able to just grab your evolution files quickly and easily when you want to copy them to a CD-ROM. With this method you are always ready.

The Official Ubuntu Wiki has a good page on cron, CronHowto, you should also read that if you want to learn to use crontab.

The crontab command has three options, 

    * crontab-l
    * crontab-r
    * crontab-e

crontab -l causes the current crontab to be displayed on standard output, (in the terminal),
to list your current crontab
To see if the cron daemon is already running, 
herman@testedgyeftbeta:~$ crontab -l
The display will feature a line like the following:
# m h  dom mon dow   command
 01 10 * * *   /usr/bin/play /home/herman/Examples/ubuntu\ Sax.ogg
That output tells me there is already one cron job running for my user account.

The -r option causes the current crontab to be removed.
will remove (i.e. delete) your current crontab.
"Don't try this at home, folks", this is just a demonstration, you should be careful not to remove anything that might be important.
herman@testedgyeftbeta:~$ crontab -r
This will have removed my old crontab, to take a peek and make sure I'll do crontab -l again,
herman@testedgyeftbeta:~$ crontab -l
no crontab for herman
I used 'crontab -l' again to check, and sure enough, it's gone.

This method uses a text editor like vi or joe or nano to edit  /var/spool/cron/crontabs files in the computer.
When you exit the editor, the new crontab file will be installed automatically.
The files in /var/spool/cron/crontabs should only be edited via the crontab command.

crontab -e  is used to edit the current /var/spool/cron/crontabs/crontab using the editor specified by the VISUAL or EDITOR environment variables.
herman@testedgyeftbeta:~$ crontab -e
If you don't like the text editor you're given:
crontab -e uses the the editor specified by the VISUAL or  EDITOR  environment variables.
If neither of the environment variables is defined, then the default editor /usr/bin/editor is used.
You may want to set EDITOR in your .bashrc because many commands use this variable.
You can find the file called .bashrc in your /home/username directory. It's a hidden file, so just click 'show hidden files'.  Let's set the EDITOR to nano a very easy editor to use:
export EDITOR=nano
This causes the text editor 'nano' to open. How to use nano

You will see a file open in your text editor, usually nano by default, (mine's nano anyway), and the file has a commented line like this (below).
# m h  dom mon dow   command
You will want to type in a line of commands in the correct format in order to set up your cron job.

 'm'   column is for minutes, you can type any number here from 0 to 59, an * means every minute.
 'h'   column is for hours, you can type any number here from 0 to 23, or * for 'every'.
 'dom' column is for 'day of the month' from 1 to 31, or * for 'every'.
 'mon' column is for 'month of the year'use a number 1 to 12 or type 'march', or * for 'any'.
 'dow' column is for 'day of the week', mon=1, tues=2, wed=3, thu=4, fri=5, sat=6, sun=7
Note: with this method there is no column for 'user' because the file itself is already user-specific.

More information to be added here soon, website under construction.

# m h  dom mon dow   command
15 3 * * *  /home/herman/all_backups/evo_bak.sh
When done press ^o (ctrl+o) to save, then press 'enter', and ^x (ctrl+x) to close.

To see if the cron daemon now running again, 
herman@testedgyeftbeta:~$ crontab -l
The display will feature a line like the following:
# m h  dom mon dow   command
15 3 * * *   /home/herman/backup_script.sh

Now all you need to do is keep an eye out for your new evodaily backup to appear in your /home/username/all_backups directory.

It will be automatically updated every day at the same time as long as you leave the cronjob running.
Email can occupy large amounts of hard disk space. Keeping a back up of all your email all the time like this doubles the amount of disk space used for your email. If you are short of disk space you may need to disable this cron job temporarily. # Placing a hash mark in front of the line in crontab will disable the operation if you want to stop it for a while.  

If you want to save a backup from any particular day, just rename the folder. You can name it anything you like, but I suggest making up a name that includes the date of the backup in it. For example: 14apr07_evolutionbackup

The main purpose of this is to make it quick and simple to copy these backups to a CD-ROM once in a while. You should copy them when you are sure you have them safely copied to CD-ROM, only then delete them to recover your hard disk space.


Make a restore script
You can restore everything separately with a series of commands or you can make a matching restore script, let's call it: evo_rest.sh
#!/bin/sh

cp -r all_backups/daily_evobkup/addressbook  .evolution/
cp -r all_backups/daily_evobkup/calendar .evolution/ 
cp -r all_backups/daily_evobkup/mail .evolution/
cp -r all_backups/daily_evobkup/memos .evolution/
cp -r all_backups/daily_evobkup/tasks .evolution/

Apply the chmod command again to enable the new shell script to be executed and check with ls -l that the file permissions are right.
herman@red:~$ chmod 0755 all_backups/evo_rest.sh
herman@testedgyeftbeta:~$ ls -l

-rwxr-xr-x 1 herman herman    262 2007-04-15 09:40 evo_rest.sh
- rw- --- ---  1 herman herman    262 2007-04-15 09:38 evo_rest.sh~

Now all you need to do to restore from all_backups/daily_evobkup will be to open a terminal and  type: all_backups/evo_rest.sh
Or, try right-clicking on the script and click 'Open', then 'Run in Terminal'.

The script will instantly overwrite your evolution files with whatever is in the backup.

If you want to restore to an earlier date, copy your present daily_evobkup folder and rename it with today's date in the name to preserve your current files.
Then just find a folder with the date you need in your all_backups folder and rename that folder: daily_evobkup   ...that will overwrite your current daily_evobkup folder and all its files. Then run the restore script. That will restore your evolution to an earlier time.




 
How to Back-up and Restore Added Software

This is mainly for more advanced users, or quick learners. First, read Ubuntu Geek's article on how to Backup installed packages on ubuntu (this is an external link to Ubuntu Geek's great site)

Then read about apt-get by ubuntu_demon, which has a link to --> A Concise apt-get / dpkg primer for new Debian users. That says we can use the command dpkg -i <package_name> to install packages.

I hope you have read those links, in other words (to summarize all of that), you just go to /var/cache/apt/archives and copy all the packages you want before you delete your old operating system and record the packages to some media or another partition.
Then when you have a new operating system and you're ready to install your old software, just copy the packages into your /home folder and use the dpkg -i command.
To test this out with a simple example I copied the package for MacSlow's Cairo-Clock from one operating system's /var/cache/apt/archives to the /home/herman directory in a newer install,
    sudo dpkg -i cairo-clock_0.3.2-0ubuntu1_i386.deb
...and it worked fine!
This was just a simple program, I haven't gotten around to trying to see what is the most I can get away with yet. I imagine very often there will be programs with dependencies.
Another thing that might be interesting to try would be leaving a lot of packages on a CD-ROM and  seeing if Add/Remove programs will take it from the CD when deb cdrom is enabled in /etc/apt/sources.list. I know that APTonCD works something like that. I haven't tried that out yet either though.
I will need to try these things out myself for a while before I will say these ideas will work well for everyone. I think probably only experienced and adventurous should do things this way for now. Use at your own risk.




  
 
Whole Partition Back-up

Complete Back-up Using File Compression    
Sometimes, using file compression to make one big tar file is the best thing to do. You can get a lot of work done a  faster that way sometimes, and squeeze more onto your back-up media too. Here's a link to a way to make a more complete back-up and restore job, using file compression.    
 
GParted Partition Back-up   
Another way to do a major back-up and restore job, which saves everything, is to use GParted  Live CD .  Just download the .iso for that from the link and burn it to a CD and give it a spin.
UPDATE: With the use of file system UUID numbers these days, this method is not as good as it was when this item was first written.
It would be better to look at aysiu's tutorial, Use PartImage

GParted LiveCD has Partimage in it. I use Partimage too now.  To start Partimage in GParted LiveCD just open a terminal and type: partimage
Following are more links,
Partimage Home Page, [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
Partimage Manual, [http://www.partimage.org/Partimage-manual_Usage](http://www.partimage.org/Partimage-manual_Usage)
One version of GParted LiveCD also has Clonezilla added to it by LarryT as well.

Copy and Paste the whole partition with GParted
This was the original method I had here, I'll still keep it here for a while in case it's useful to anyone. This was my favorite method for a long time. Filesystem UUID numbers have now made this method a little bit more complicated than it used to be. With GParted, the new partition will be given the original partition's UUID number, however it will have a new partition number.
The original partition, on the other hand, retained its partition number, and but was given an new filesystem UUID. This means it will be necessary to check both /etc/fstab and also grub's menu.lst to make sure they have the current UUID numbers.

Backing up with GParted
It's easy to resize your Ubuntu operating system to as small as possible and just copy and paste the whole thing to an area of spare disk space.
That will be a fast and easy way to back up everything, including added software and system settings, the whole lot. It only takes me about ten minutes to copy and ten minutes to restore.
Most people would want to remove some of their stored data first in order to shrink the partition to a very small size.

Restoring with GParted
You just copy the back-up copy of the partition you made earlier and paste it. Then you re-size it to the size you want again. Be sure to delete the old partition first, though, to make sure you get the same partition numbers as you had before. If you get different partition numbers you will need to re-install GRUB and edit /etc/fstab with the new numbers.
    
 

Back to Top

---

### Post by PmDematagoda on 2007-10-07
Thanks for spending your time on finding this Pumalite, I appreciate it:).

---

### Post by mdebusk on 2007-10-07
> **Protagonistics said:**
> is there any program I can use that uses an easy, GUI where I can back up my most treasured files?

The Engaget blog has instructions on [automatically backing up to a remote server via ssh and rsync](http://www.engadget.com/2007/03/21/how-to-automatically-back-up-your-computer/). I found the link on [Lifehacker](http://lifehacker.com).

It isn't a GUI program, but once it's set up it really doesn't need to be.

---

### Post by Protagonistics on 2007-10-07
Mdebusk said: 
The Engaget blog has instructions on automatically backing up to a remote server via ssh and rsync. I found the link on Lifehacker.

It isn't a GUI program, but once it's set up it really doesn't need to be. 

Ok, that looks like a great site with good instructions-- but the part that really concerns me is HOW to find a remote server to stash my files- how does one find one of these if one owns just a laptop like me? Do all the linux nerds out there have a friend with an old computer built just for storage that they ssh to or can I write a nice email to Mozy and ask them-- and what in the world do I ask them for?

To quote Engadget: 
"Once you've decided where to keep your data, and what you want to backup on your laptop or workstation, you'll need the tools to keep things rolling."

But how do I decide? What do you do *to* decide? 
Again, I hope that's clear enough.
thanks.

---

### Post by mdebusk on 2007-10-07
> **Protagonistics said:**
> Ok, that looks like a great site with good instructions-- but the part that really concerns me is HOW to find a remote server to stash my files- how does one find one of these if one owns just a laptop like me?

The simple thing to do is get some inexpensive hosting. I use HostMonster.

---

### Post by mdpalow on 2007-11-27
check out the link in my signature below. It's easy enough..

---

### Post by bern1939 on 2007-11-29
I hope you do not mind I sending a query on the very excellent posting on 'Automatic Backups'

I have followed it line by line (even copying/pasting) but keep getting this msg.

bernard@bernard-desktop:~$ *all_backups/evo_bak.sh*
cp: target `/all_backups/daily_evobkup/' is not a directory: No such file or directory
cp: target `/all_backups/daily_evobkup/' is not a directory: No such file or directory
cp: target `/all_backups/daily_evobkup/' is not a directory: No such file or directory
cp: target `/all_backups/daily_evobkup/' is not a directory: No such file or directory
bernard@bernard-desktop:~$ all_backups/evo_bak.sh

The strange thing is that the sub-folder 'daily_evobkup' does appear in the folder 'all_backups' but contains no files.

Also in your instructions it says..."We should see a new directory appear inside all_backups named: *dailyevo_bkup*. Should that not read *daily_evobkup*??

Thanks

Bern

---

### Post by shanepardue on 2008-01-28
> **mdebusk said:**
> The simple thing to do is get some inexpensive hosting. I use HostMonster.
Hostmonster doesn't let you store ANY copyrighted material even if you own it legally. I would not recommend their services to anyone.

---

