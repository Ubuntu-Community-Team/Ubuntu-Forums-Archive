---
title: "problem with cd commands"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by mahmater on 2008-04-03
hey.. I'm an ubuntu newbie.I have a problem using the cd commands despite the tutorials I read about it. how can I for eg unzip file x in folder y on my desktop from the terminal?

I cannot acess folder -say conference- on my desktop using this command:

 cd home/desktop/conference
thanks for help

---

### Post by privaterolf on 2008-04-03
You're missing a / before home

```
/home/yourusername/Desktop/conference/
```

Be aware that for EVERY user, the Desktop folder has a capital D.

You're also missing your user name, which will be in lower case letters.

By the way, right click and use the archive manager to unzip, hit extract on the toolbar icons at the front, and it should let you extract to whatever folder you want. ;)

---

### Post by mahmater on 2008-04-03
great dear friend! I now got access to the folder. concerning the archive manager it cannot,it says that it doesn't support the rar file. I'm now trying to install ark.

many thanx

---

### Post by privaterolf on 2008-04-03
> **mahmater said:**
> great dear friend! I now got access to the folder. concerning the archive manager it cannot,it says that it doesn't support the rar file. I'm now trying to install ark.

many thanx

Your welcome.

Post back if you need any more help.

---

### Post by mmasroorali on 2008-04-03
cd /path/to/y
takes to you to y
say if y is in your home directory, you can type 
 cd ~/y 
or 
 cd /home/y
or 
 cd
 cd y

Then type
unzip -v x.zip 
or unzip -v /path/to/x.zip
That gives you a list of files that will be extracted.
If you are happy, then type
unzip  /path/to/x.zip

---

### Post by mmasroorali on 2008-04-03
Use unrar to handle rar files. It is installed by default.

---

### Post by bodhi.zazen on 2008-04-03
You can use ~ as shorthand for /home/user_name

cd ~/Desktop/conference/

you can use ~user_name for other people's home

You can use teh tab key to complete directories / file names

cd ~/De<tab>/conf<tab>

---

### Post by mahmater on 2008-04-04
indeed I'm more than satisfied,I appreciate ur help. All of you. I'm now trying to apply and experiment with these tips.

---

### Post by mahmater on 2008-04-04
sorry I'm stuck again.

I typed : " cd ~/qBT_dir" to get access to qbittorent folder in my home.
 and it gives me this : ~/qBT_dir$ 
  (now what I should type to view the contents of the my downloads? of course I could do this with "ls", but suppose I want to delete a video clip x how can I do it?

u have to be somewhat patient with me. 
many thansx.

---

### Post by hurtstotalktoyou on 2008-04-04
Why don't you just try going to the dropdown menu on the top of your screen:

Places > Home Folder

Then double-click on qBT_dir

Then you should see all your files in a GUI.

However, if you *really* want to see the files in terminal, just type "dir".  If you have a lot of files you'll have to scroll up and down to see them all.

---

### Post by Tatty on 2008-04-04
> **mahmater said:**
> sorry I'm stuck again.

I typed : " cd ~/qBT_dir" to get access to qbittorent folder in my home.
 and it gives me this : ~/qBT_dir$ 
  (now what I should type to view the contents of the my downloads? of course I could do this with "ls", but suppose I want to delete a video clip x how can I do it?

u have to be somewhat patient with me. 
many thansx.

To delete files from the command line... [http://en.wikipedia.org/wiki/Rm_%28Unix%29]("http://en.wikipedia.org/wiki/Rm_%28Unix%29")

---

### Post by bodhi.zazen on 2008-04-04
Naw, learn the command line, you will not regret it.

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
	[http://www.reallylinux.com/docs/admin.shtml](http://www.reallylinux.com/docs/admin.shtml)
	[http://www.reallylinux.com/docs/guru.shtml](http://www.reallylinux.com/docs/guru.shtml)
	[http://linuxcommand.org/](http://linuxcommand.org/)
	[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by mahmater on 2008-04-05
thanx *Hurtstotalktoyou*. the point is that I just want to learn how I can manage it via commands. i'm trying to learn new things ...that's it.

---

### Post by lswest on 2008-04-05
some useful commands:

*rm* - **delete/remove files or empy folders (with the argument "-r" can also delete full folders)**
*ls* - **lists file in current folder (or specified path), with the argument "-l" shows the files in long format, with permissions**
*cp* - **copies files/folders, if you want to copy all files/folders within a directory, use the recursive argument ("-R")**
*mv* - **moves files, if you want to move all files within a folder use the recursive argument ("-R") and a "wildcard" ("*") from the directory (e.g. cd there first)**

---

### Post by mahmater on 2008-04-06
many thanx for ur help. indeed my problem is not with which command to use to remove a file,but with how can I access a file through a cd command. My example is this:

 my home file contains a folder named **_qB_**T, and in this folder I want to remove a video called **_REMIX_**.

now I typed :
 
cd ~/qBT_dir 

and it led me to the folder :

~/qBT_dir$

My question is : how can I access  what's in the folder to remove it ,unzip it or whatever?
I could do this easily by going to home folder and manually opening the folder but I want to know **_how can I do it with a command_**.

---

### Post by bodhi.zazen on 2008-04-06
> **mahmater said:**
> many thanx for ur help. indeed my problem is not with which command to use to remove a file,but with how can I access a file through a cd command. My example is this:

 my home file contains a folder named **_qB_**T, and in this folder I want to remove a video called **_REMIX_**.

now I typed :
 
cd ~/qBT_dir 

and it led me to the folder :

~/qBT_dir$

My question is : how can I access  what's in the folder to remove it ,unzip it or whatever?
I could do this easily by going to home folder and manually opening the folder but I want to know **_how can I do it with a command_**.

It sounds as if you are asking how to access the file via the comand line ?

cd = "change directory"

You can see the contents of a text file with :

nano /path_to_file

ie 

```
nano ~/qBT_dir/file
```

To remove (delete) a file use

```
rm file_to_delete
```

To open a file with an ( X ) application use the name of the application and name of file

```
gedit ~/qBT_dir/file
```

And on, see the links I gave you ...

---

