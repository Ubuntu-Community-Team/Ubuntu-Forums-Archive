---
title: "How do you create a batch file to run commands?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2006-06-25
I am trying to write a little script to backup all my files I want using rsync

rsync  -urv /a /b
rsync -urv /c /b
rsync -urv /d /b


How do I make a batch file that can execute when I double click on it?

Thanks!

---

### Post by 23meg on 2006-06-25
Right click the file, go to Properties / Permissions, tick the "Execute" box for "Owner".

---

### Post by boom2k1 on 2006-06-25
Thanks!
that's useful.

Which extension should I save it as?

I notice that when I double click on it, a popup window reads, "Do you want to run .. or display content"

Is there anyway to make it run by default?
Thanks!

---

### Post by 23meg on 2006-06-25
[QUOTE=boom2k1]
Which extension should I save it as?
[/quote]Doesn't matter, but it's a convention to use .sh .
[QUOTE=boom2k1]I notice that when I double click on it, a popup window reads, "Do you want to run .. or display content"

Is there anyway to make it run by default?
Thanks![/QUOTE]In Nautilus go to Edit / Preferences / Behaviour / Executable Text Files.

---

### Post by boom2k1 on 2006-06-25
And also, even when I click "RUN in terminal", it closes when the script is finished.

Is there any ways to get rid of that default close?
(i.e. user needs to press a key before it quits)

Thanks!

---

### Post by aysiu on 2006-06-25
[QUOTE=boom2k1]
I notice that when I double click on it, a popup window reads, "Do you want to run .. or display content"

Is there anyway to make it run by default?
Thanks![/QUOTE] Yes, but it'll do it for every executable file.

---

### Post by boom2k1 on 2006-06-25
Thanks! Great help! :)

Anyone knows about the "Get a key" command to prevent it exit before I can see what happened?
(I need that because I would like to view what changes were made to the files)

Does anyone know how I can create a log of the changes using rsync?
Thanks!

---

### Post by 23meg on 2006-06-25
[QUOTE=boom2k1]And also, even when I click "RUN in terminal", it closes when the script is finished.

Is there any ways to get rid of that default close?
(i.e. user needs to press a key before it quits)

Thanks![/QUOTE]
Add the command "read" to the end of the script.

---

### Post by boom2k1 on 2006-06-25
THank you! That's perfect!

---

### Post by boom2k1 on 2006-06-25
Linux is SO POWERFUL.
I am so impressed

sudo mount /dev/sda1
rsync -urv /documents/ /PrimaryStorage/Laptopbackups/documents/
read

is all I need to backup the whole partition to my external drive.

and all I need is to double click on the icon to perform the backup!
Better yet, I have a feeling that if I write another mini script, I would be able to perform the backup automatically (i.e. every week!)

Thanks!

---

### Post by 23meg on 2006-06-25
bash never fails to impress new power users.
> Better yet, I have a feeling that if I write another mini script, I would be able to perform the backup automatically (i.e. every week!)
You don't need another script for that; do a search for cron and anacron to figure out how to use them to perform periodical tasks.

---

### Post by markayler on 2008-05-15
I am trying to create a batch file that runs a few commands but it's erroring out.
Here is my Batch File

#!/bin/sh
input_reset ipaddress_test > output.txt

root@pc114-0108:/usr/local/bin/misc_scripts# ls -al
total 32
drwxr-xr-x 2 root root 4096 2008-05-15 11:30 .
drwxr-xr-x 5 root root 4096 2008-04-30 14:46 ..
-rwxr-xr-x 1 root root   50 2008-05-15 10:44 batch_reset
-rwxrwxrwx 1 root root   55 2008-05-15 08:48 input_reset
-rwxrwxrwx 1 root root 1231 2008-04-30 14:47 ipaddress_sort
-rwxrwxrwx 1 root root   12 2008-05-15 08:51 ipaddress_test
-rwxrwxrwx 1 root root  869 2008-05-15 08:50 ipaddress_test~
-rwxrwxrwx 1 root root 2374 2008-05-15 08:53 reset.exp
root@pc114-0108:/usr/local/bin/misc_scripts# 

I get this error when trying to run the batch file from CLI. Maybe i'm executing the file wrong?

root@pc114-0108:~# /usr/local/bin/misc_scripts/batch_reset 
/usr/local/bin/misc_scripts/batch_reset: 2: input_reset: not found
root@pc114-0108:~# 


You might want to know what input_reset and ipaddress_test is. See below

root@pc114-0108:/usr/local/bin/misc_scripts# more input_reset 
cat $1 | while read ipaddr
do
./reset.exp $ipaddr
done


That's my input_reset file. reset.exp is a script file that logs into a remote switch. It gets the Ip address for the switch from the ipaddress_test file. As you seen above, reset.exp is also in the same directory.

Any ideas? I'm new to this stuff but love it.

---

### Post by markayler on 2008-05-15
FIXED IT. 

Before
#!/bin/sh
input_reset ipaddress_test > output.txt

After
#!/bin/sh
sh input_reset ipaddress_test > output.txt


The problem was my batch file. I guess it didn't know what to do with input_reset. I figured that #!/bin/sh would automatically put that 'sh' before input_reset.

---

### Post by inportb on 2008-05-15
If input_reset is not in a directory on the $PATH, you gotta use the dot-slash convention:

./input_reset

---

### Post by markayler on 2008-05-16
Well, I got my batch file to run my script but I can't get at -f <file location> or crontab -e to run the batch file. 

My crontab -e file looks like this(runs at 9:08am, Friday): 

# m h  dom mon dow   command
08 9    * * 5   root /usr/local/bin/misc_scripts/batch_reset

The log (/var/log/syslog) says this:

May 16 09:02:01 pc114-0108 /USR/SBIN/CRON[26484]: (root) CMD (root    /usr/local/bin/misc_scripts/batch_reset)

But...it doesn't run. Anyone got some pointers?

---

### Post by markayler on 2008-05-16
I got it to work...

I was missing the full path inside one of my files. I learned how to set up my mail...so that I could receive the errors.

---

