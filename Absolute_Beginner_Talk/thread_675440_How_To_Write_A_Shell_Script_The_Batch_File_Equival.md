---
title: "How To Write A Shell Script: The Batch File Equivalent"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by AxZym on 2008-01-22
Question: How do I go about writing a batch file for Ubuntu?

Looking for a quick primer on writing a small script to execute a number of commonly executed commands.

In Windows, I am accustomed to writing a batch file that is typically just a simple collection of several commands, often separated by a line break (or a carriage return).

In researching the subject, I've learned that in Linux, this is referred to as a shell script (this language is also used interchangeably in Windows.) 

So, in effort to get my feet wet and to further my understanding of Ubuntu, I thought I'd post my latest challenge to the Ubuntu Forums.

Challenge: Write a shell script that copies a large file from one location (HDD) to another location (mounted USB HDD) and allows me to monitor the transfer status (i.e. 50% complete, 98% complete, Done! etc.)

This is what I have so far:
```
#Copy Large File To Another Drive
#Created 2008-01-22

sudo cp /home/<username>/folder/largefile.ext /media/<mounted_drive>/destination/
read
```

I saved the file as tfile.sh > Right-clicked on the file in the File Browser > Selected "Properties" > Navigated to "Permissions" Tab > Put a check in "Allow executing file as program"

To make the file easily accessible, I created a shortcut on the desktop. Right-clicked on the Desktop > Selected "Create Launcher" > In "Type", I selected "Application in Terminal" > Gave it a name > and selected "tfile.sht" from my Home folder via the "Browse" button > Finished

Also, note on the last line of the tfile.sh file, I included the "read" command, thinking that it would allow me to see output from the command (such as complete) but when executed via the Desktop Shortcut it just opens a blank Terminal window and keeps it open perpetually.

Right now, I'm simply monitoring the HDD activity light to "gauge" whether the transfer is complete. I then cross my fingers, close the Terminal window and hope that I can unmount my USB drive. :)

Any insight on how I can write shell script that will return some indication of the progress of the file copy would be greatly appreciated.

Thanx,
AxZym

---

### Post by bodhi.zazen on 2008-01-22
zenity will do it for you

see man zenity

---

### Post by Xavieran on 2008-01-22
You could add a zenity --progress --pulsate to that...
ie.
[PHP]#Copy Large File To Another Drive
#Created 2008-01-22

sudo cp /home/<username>/folder/largefile.ext /media/<mounted_drive>/destination/ | zenity --progress --pulsate
[/PHP]

Here is a md5sum script that will be able to help you understand zenity a bit more...it tells you if an md5sum has a match or not...but it can never make a match because md5sum includes the exact path to your .iso...:)

[PHP]cdiso=`zenity --file-selection --title "Please choose the .iso file to md5sum check..."`
md5sum=`zenity --entry --text "Please copy and paste the relevant md5sum..." --title "md5sum checker"`
zenity --info --title "md5sum checker" --text "Please wait...md5summing takes a long time :)"
compare=`md5sum $cdiso`
if [ $compare == $md5sum]; then
    zenity --info --title "md5sum checker" --text "The md5sums are the same for $cdiso and the md5sum that you gave."
else
    zenity --info --title "md5sum checker" --text "The md5sum you gave is different from the .iso\nResults:$compare"
fi
exit[/PHP]

---

### Post by AxZym on 2008-01-22
Good Day Xaverian,

Thank you for your response. I'm trying zenity but currently all I'm getting is a Box titled "Progress" with a "Running..." dialog. 

It's been running for a few minutes with no change in status.

Please see my code below:

```
#Copy Large File To Another Drive
#Created 2008-01-22

sudo cp /home/<username>/folder/largefile.ext /media/<mounted_drive>/destination/
read | zenity --progress --pulsate
```

Does anybody have a suggestion?

Thanx,
AxZym

---

### Post by bodhi.zazen on 2008-01-22
First, your script does not need to be run as root.

> #!/bin/bash
#Copy Large File To Another Drive
#Created 2008-01-22

#All one line:

cp /home/<username>/folder/largefile.ext /media/<mounted_drive>/destination/ | zenity --progress --pulsate

---

### Post by Xavieran on 2008-01-22
```
#!/bin/bash
#Copy Large File To Another Drive
#Created 2008-01-22

#All one line:

cp /home/$HOME//folder/largefile.ext /media/<mounted_drive>/destination/ | zenity --title "Moving Files" --text "Moving..." --progress --pulsate 
```

Also, what is read there for,I think it might be what is not causing it to show any progress...I just ran read and it didn't do anything...

EDIT:Yes,read is not what you should be using there...either use zenity or read -p "Finished" ...

---

### Post by Dr Small on 2008-01-22
Maybe I am missing something, but isn't that supposed to be:
```

#Copy Large File To Another Drive
#Created 2008-01-22

sudo cp /home/<username>/folder/largefile.ext /media/<mounted_drive>/destination/ | zenity --progress --pulsate
```

???

---

### Post by bodhi.zazen on 2008-01-22
I think you need to remove "sudo" from the script or it will hang expecting a password.

If you need to run it as root:

sudo /path/to/script

Also, consider adding user scripts to /home/user/bin and adding /home/user/bin to your $PATH

---

### Post by AxZym on 2008-01-22
Good Day bodhi.zazen,

Thank you for your response.

I have two questions for you:

1. You wrote:
> **bodhi.zazen said:**
> First, your script does not need to be run as root.

Can I copy files from any location without using Super User Do (sudo)? What if the file I am attempting to copy is not located in the Home folder?

2. In that "#" comments out a line what purpose does the "#!/bin/bash" serve? Should I add this line?

In response to the succeeding post, I have since removed the "read" to no avail. The same dialog box is displayed.

Thanx,
AxZym

---

### Post by Xavieran on 2008-01-22
```
#!/bin/bash
#Copy Large File To Another Drive
#Created 2008-01-22

#All one line:
file=`zenity --file-selection --title "Select a file to move"`
cp $file /media/<mounted_drive>/destination/ | zenity --title "Moving Files" --text "Moving..." --progress --pulsate
```
You should be able to copy files from anywhere (As long as you have permission to view them...)
#!/bin/bash is used so that when you double click and choose run,it will know what to run it as...

---

### Post by bodhi.zazen on 2008-01-22
IMO, Zenity documentation is hard to find and the best source is the man pages which give several examples.

Type ```
man zenity
``` in a terminal. type "q" to exit (that really is the best way to learn zenity).

Permissions are different, and depend on the file system. That is another topic altogether, but you should be able to run this script without escalating to root with the proper permissions.

I will try to look in on this thread a little later, but suggest you look at some bash scripting sites.

[http://ubuntuforums.org/showthread.php?&t=233564](http://ubuntuforums.org/showthread.php?&t=233564)

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc2](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc2)

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

[http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

---

