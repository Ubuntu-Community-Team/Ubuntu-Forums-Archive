---
title: "Opera crash"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by atlas77 on 2005-11-10
Hi!

I had installed Opera a few days ago and it was running all right until yesterday, when it did not launch and i was unable to connect to the net. Mozilla did connect at the same time, though. I then removed (or at least, tried to remove) Opera and downloaded three versions of the browser from the Opera website (8.5, 8.5 static and 9.0) but I was unable to install any of them. I typed "sudo dpkg -i opera< file name >" in the terminal then I got something like this: Unable to reach archive, no such directory exists, and Error occured when trying to process <file name>. 
Now I have very little experience with LINUX so I don't even know how to properly remove a file / directory so maybe I still have an active version of Opera. Is it possible that my problem has something to do with this? Also, could anyone tell me how to remove a directory and how to make sure it has been removed?

Thanks for taking time to answer my question!!!

---

### Post by Lambert on 2005-11-10
> I had installed Opera a few days ago and it was running all right until yesterday, when it did not launch and i was unable to connect to the net. Mozilla did connect at the same time, though. I then removed (or at least, tried to remove) Opera and downloaded three versions of the browser from the Opera website (8.5, 8.5 static and 9.0) but I was unable to install any of them. I typed "sudo dpkg -i opera< file name >" in the terminal then I got something like this: Unable to reach archive, no such directory exists, and Error occured when trying to process <file name>.  
You have to make sure you're in the same directory as the package or type the full path name. So if you saved the download to /home/<name>/download/<opera_download> then you would move to the directory by typing in the terminal```
cd /home/<name>/download
``` then type sudo dpkg -i <package_name>
quick tip: you don't have to type out the complete package name, type in the first couple leters then hit the tab key, it will autocomplete the file name, neat feature in bash.


> Now I have very little experience with LINUX so I don't even know how to properly remove a file / directory so maybe I still have an active version of Opera. Most program will be installed through dpkg or apt-get or synaptic. To remove it you can type
```
sudo dpkg purge <package_name>
``` 
purge actually deletes everything including the config files. If there is a possiblity of reinstalling later you can replace that with -r and it will uninstall the app but leave the config files.

 > Is it possible that my problem has something to do with this? Also, could anyone tell me how to remove a directory and how to make sure it has been removed? 
This is a powerful command as when you run it the files is gone.

```
rm /<path_to_file
``` 
Why I say this is powerful is that if you run it to the wrong path or use some meta characters you can wipe out important files. I suggest running ```
 ls -a /<path>
``` and it will show you the exact files that will be removed. then rerun replacing ls with rm. You won't use rm to uninstall packages though, just delete a file or set of files.

man is a good command to learn. The pages are a little hard to understand at first but you will want to take some time and familiarize yourself with man. type ```
man ls
``` to see what it looks like.

Most packages you want you can find in the repositories. If it's not there look for a file ending with .deb which can be installed through the dpkg command. look at the man page for dpkg. man dpkg

[here's a good link to installing packages from synaptic]("https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29")

Lastly type opera into search on the forum and you'll find posts about installing and problems. When I was usinb opera I did not use the ubuntu version but the static.deb version. it worked better for some reason and solved some plugin problems I was having.
[URL="https://wiki.ubuntu.com/SynapticHowto?highlight=%28synaptic%29"] 
[/URL]

---

### Post by atlas77 on 2005-11-11
Whoaa, thanks for the extensive tutorial!!:D I'll try these as soon as I get back to my PC.

In the meantime, both apt-get and Synaptic have become useless, I cannot download any packages from the reps any more, it doesn't connect for some reason (possibly i messed with some files I shouldn't have touched with such little knowledge of the system). So I've decided to reinstall Breezy and start from scratch but I have a very noob question which I hope you can answer though it has nothing to do with Opera: **How do I reinstall Breezy?** I've tried it once already but the result was a second Breezy install so I had Win XP and 2 Ubuntu Brezzy installed. What exactly do i have to do apart from booting from the CD-ROM?

Thanks in advance!!!

Peter

---

### Post by Lambert on 2005-11-11
when you install you get to a screen that looks like [COLOR=Blue][this.]("http://www.howtoforge.com/images/perfect_setup_ubuntu_5.10/img_10.gif")

[COLOR=Black]Chose the manual edit option.

Choose the partitions you want, I would have something like this. (dual  boot)

#1  - windows partition XXGB
#2  - xxGB FS /
#3  - xxgb FS /home
#4  - xxgb FS swap

FS= the file system you want to use; ext2 ext3 reiserfs

And of course any other partions that you may have data on would be in this list.

To add these just choose the partition, enter, then set the options.
If you don't need a partition (maybe the second ubuntu partition can be deleted.) If you want to start from scratch delete all the partions you don't need and highlight the free space, you'll have an option to create a partion, set it up to your liking.

There is an option you can choose [COLOR=DarkRed]Help on partitioning [COLOR=Black]to read more.

Also post back if needed, this is kind of a vague explanation, take your time so you don't lose any data and post back if you have any questions or need clarification.




[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by atlas77 on 2005-11-13
Thank you, I still haven't been able to try re-partitioning but it shouldn't be a problem, even if I deleted anything important I have everything saved...

Once again, thanks for helping me out on this!

---

