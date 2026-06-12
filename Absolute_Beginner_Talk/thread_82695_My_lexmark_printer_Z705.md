---
title: "My lexmark printer Z705"
date: 2005-10-27
forum: Absolute Beginner Talk
---

### Post by cjpkot on 2005-10-27
I've been trying to print a document.  I selected as a default printer and ran a test.  It is not working.  I've got 4 USB ports.  I went to lexmark to see if they had a fixs.  I believe not.  I know that the lexmark printers are in the selector for printers but no lexmark printer selected seems to work.
Thxs

---

### Post by Iandefor on 2005-10-27
Try [this page]("http://www.ubuntuforums.org/showthread.php?t=49714&")

---

### Post by cjpkot on 2005-10-30
I've down loader the lexmark 600 LE linux file as discribed on the reply sent by Landefor.
I keep getting command error messages.  The only thing I was able to do was mkdir.
The rest of the commands it said it didn't reconize file or directory.
I used terminal to enter commands.
Do I need to load anything from synaptic package manager to get the commands to work.

---

### Post by Mustard on 2005-10-31
cjpkot, it would be helpful if rather than describing in vague terms what is not working, you actually copy and paste the errors into this thread.  In your paste include the command you typed in and the output of those commands.  Error messages can give very specific clues to what the problem is.  Without them you make it quite difficult for others to help you.

---

### Post by cjpkot on 2005-10-31
Thankyou,  I will try to be more specific.
-I down loaded CJLZ600LE to my Desktop-

-This is what I did first.-
$ mkdir lexmark  

-next I did this step and I got file not found
$ mv CJLZ600LE-CUPS-1.0-1.TAR.gz lexmark # move the package to a folder. optional, but recommended. 

-next I thought I would do the instruction below and I got file not found-
$ tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.

---

### Post by cjpkot on 2005-11-01
I was able to create the directory as discribed.
Next command didn't work  ~$ mv CJLZ600LE-CUPS-1.0-1.TAZ.gz lexmark
mv: cannot stat `CJLZ600LE-CUPS-1.0-1.TAZ.gz': No such file or directory

Please advise  Is my terminal requiring download through synaptic
Some things I can do but to move file to a new folder didn't work 
Thanks

---

### Post by Mustard on 2005-11-02
cjpkot, the terminal normally starts, by default, using your /home/username directory, also know in shorthand as your ~/ directory.  You can confirm what directory is the current 'working directory' by entering the command, pwd.  Since you saved the file to your /home/yourusername/Desktop, the shorthand for this folder/directory is ~/Desktop.  The tilda, '~', is shorthand for /home/username/. 

In your case you saved CJLZ600LE-CUPS-1.0-1.TAR.gz to the ~/Desktop.  So to change the current directory you would use the cd command like tthis..

```
cd ~/Desktop #change current directory to /home/username/Desktop, remembering that the  '~', or tilda is shorthand for /home/username/

I use the above command because it is the equivalent to this command below, but not knowing your username, I can't know it's final form ie I can't know what to substitute for the 'username' part of the path to directory.

cd /home/username/Desktop 
(substituting your actual username for the word 'username' in the example
```

Having changed the 'working directory' you can now list the contents of that directory with the ls command..
```
ls #list contents of current directory
```

From there you will be able to work on the CJLZ600LE-CUPS-1.0-1.TAZ.gz with other commands.

To move the file to the ~/lexmark directory, you can do this,

```
mv CJLZ600LE-CUPS-1.0-1.TAZ.gz ~/lexmark/ 
#move the file CJLZ600LE-CUPS-1.0-1.TAR.gz to the /home/username/lexmark/ directory
```

Once you have moved the file to the ~/lexmark/ directory or folder, you can use the tar command you attempted by changing you working directory to the location the file is in now....

```
cd ~/lexmark #change current directory to /home/username/lexmark/
```

then you can use the tar command on the file in question..

```
tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz
```

You can find manuals for all these commands in your terminal by typing this

```
man cd #manual for cd command
man mv #manual for mv command
man tar #manual for the tar command

```

You also may find these links below handy as further reference.

[https://wiki.ubuntu.com/BasicCommands]("https://wiki.ubuntu.com/BasicCommands")
[http://www.linuxcommand.org/]("http://www.linuxcommand.org/")

---

### Post by cjpkot on 2005-11-03
I have gone this far.  tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
 tail -n +143 z600cups-1.0-1.gz.sh
After entering this code I got this
\uffff\uffffn\uffff\uffffYcarl@69-11-41-40jerome:~/Desktop/lexmark$ 62;9;c62;9;c62;9;c62;9;c62;9;c;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c

Then I entered this command  tar -xvzf install.tar.gz
and got this response
arl@69-11-41-40jerome:~/Desktop/lexmark$ tar -xvzf install.tar.gz
tar: install.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
 What do I do next?
Thankyou

---

### Post by cjpkot on 2005-11-03
I have gone this far. tar -xvzf CJLZ600LE-CUPS-1.0-1.TAR.gz # extract the driver.
tail -n +143 z600cups-1.0-1.gz.sh
After entering this code I got this
\uffff\uffffn\uffff\uffffYcarl@69-11-41-40jerome:~/Desktop/lexmark$ 62;9;c62;9;c62;9;c62;9;c62;9;c;9;c62;9;c62;9;c62;9 ;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c 62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62 ;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9 ;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c 62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62 ;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9;c62;9 ;c62;9;c62;9;c

Then I entered this command tar -xvzf install.tar.gz
and got this response
arl@69-11-41-40jerome:~/Desktop/lexmark$ tar -xvzf install.tar.gz
tar: install.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
What do I do next?
Thankyou

---

### Post by Iandefor on 2005-11-03
Open up Nautilus and go to the directory where CJLZ600LE-CUPS-1.0-1.TAR.gz is. Right click it, and choose "extract here"- do the same for install.tar.gz. It's a little less prone to error than using the command line. But I would suggest deleting the folders that both the compressed files made beforehand, if any were.

---

