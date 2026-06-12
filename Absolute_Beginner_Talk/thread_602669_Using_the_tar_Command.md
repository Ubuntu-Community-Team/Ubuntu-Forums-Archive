---
title: "Using the tar Command"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by shredfitz on 2007-11-04
[COLOR="Orange"]Hello. My first post in awhile  here and it is related to a linux administration class that I am enrolled in at school.

We were given Red Hat to install, but the instructor said we could use any distro. I already have feisty fawn installed, so I am using that for the class.

Anyway, this is the problem:

I am doing a 'hands-on' project from the textbook ( The Complete Guide to Linux Administration, published by Thompson Course Technology).

The project's purpose is to ' experiment with the tar command to create a simple data archive file and then extract the contents of that file into another directory.

So i will list the steps below and tell you where I am having the problem. Verbatim, from the text starting below:
[/COLOR]
1. Log in to Linux using your regular user account[COLOR="DarkOrange"] (got it)[/COLOR]

2. If you logged in using a graphical login window, open a comman d-line window.[COLOR="DarkOrange"] (got it)[/COLOR]

3. Use the **su** command to change to root. Enter the password when prompted.[COLOR="DarkOrange"] (got it)[/COLOR]

4. Change to the /etc/init.d directory by entering :** cd /etc/init.d**[COLOR="DarkOrange"] (got it)[/COLOR]

5. Review the file names and file permissions for the various configuration files in this directory by entering : **ls -l | less** [COLOR="DarkOrange"] (got it)[/COLOR]

6. Press **q** to exit the* less* command when you have finished reviewing the output of the *ls* command. Create a tar archive of the configuration files in the /etc/init.d directory by entering:** tar cf /tmp/testing.tar /etc/init.d/***

Because you are including the path name to both the testing .tar archive file and the directory containing the information you want to archive, you can execute this command from any location on the system.

[COLOR="Orange"](the previous step, #6, is where the trouble begins. After I enter in the command, I am given a message that says 'tar: Removing leading `/' from member names' )[/COLOR]

7. Enter a similar command, this time including the *v* option as in

** tar cvf /tmp/testing2.tar /etc/init.d/***

After you execute this command, you see a list of all the files in the /etc/init.d directory appear on the screen as each is added to the file archive[COLOR="Orange"] (ok, this seemed to work)[/COLOR]

8. Change to your home directory , /root , by entering the **cd** command. [COLOR="Orange"](got it)[/COLOR]

9. Use the **ls** command to examine the contents of your home directory. Make certain you do not have a file called network in your home directory. You shouldn't, but if you do from a previous exercise, rename it to something else to complete this project.  [COLOR="Orange"](ok, that seems to be fine)[/COLOR]

10. Use the *x* option of the *tar* command to extract a single file from the tar archive that you just created, by entering

**tar xvf /tmp/testing2.tar etc/init.d/network**

The file is placed in your current directory. Because the* v* option the file name is printed to the screen as it is extracted. 

[COLOR="Orange"](on that step I get the following: tar: etc/init.d/network: Not found in archive
                                                    tar: Error exit delayed from previous errors)
[/COLOR]
11. Use the **ls** command to review the contents of your home directory. Do you see a file called network? Look for a directory called etc.

[COLOR="Orange"](nope, i do not see a file called network nor do I see a directory called etc.)[/COLOR]

________________________________________________--

[COLOR="Orange"]Okay so there are a few more steps left in the project, but I cannot continue with them due to the problems I am encountering in the previous steps.

I am not looking for someone to do my work for me, I just cannot understand what I am doing wrong. I am following the directions exactly. I think my problems stem from step 6.

This course is online and I have posted a message on the student help board but haven't gotten a response so I figured I'd post here to see if anyone can help me. Thanks for your time.[/COLOR]

---

### Post by sisco311 on 2007-11-04
6. [http://www.linuxquestions.org/questions/linux-general-1/bintar-removing-leading-from-member-names-269508/](http://www.linuxquestions.org/questions/linux-general-1/bintar-removing-leading-from-member-names-269508/)

10. you are trying to extract the etc/init.d/network file. in ubuntu it's etc/init.d/networking.

```
tar xvf /tmp/testing2.tar etc/init.d/networking
```this will also recreate the folder structure to the single file unless you use the -O (stdout) option and direct that to a different file.

```
tar xvf /tmp/testing2.tar etc/init.d/networking -O > networking
```

---

### Post by shredfitz on 2007-11-04
Thanks Sisco

---

### Post by shredfitz on 2007-11-04
Ok Sisco or anyone else reading this-

The instructor wants us to do this :[COLOR="DarkGreen"] Using the “history” command (look it up if you need to), pipe the relevant commands (only the relevant commands) you used in the project to a file named “tar_project43_history.txt” and place it in the drop box with a file named “tar_listing.txt” which, as you might of guessed, is the listing of the contents of the tar file. NOTE: I do not want the tar file itself.[/COLOR]


suggestion?

---

### Post by mali2297 on 2007-11-04
> **shredfitz said:**
> Ok Sisco or anyone else reading this-

The instructor wants us to do this :[COLOR="DarkGreen"] Using the &#8220;history&#8221; command (look it up if you need to), pipe the relevant commands (only the relevant commands) you used in the project to a file named &#8220;tar_project43_history.txt&#8221; and place it in the drop box with a file named &#8220;tar_listing.txt&#8221; which, as you might of guessed, is the listing of the contents of the tar file. NOTE: I do not want the tar file itself.[/COLOR]


suggestion?

```

history 30 > tar_project43_history.txt
tar tf /tmp/testing.tar > tar_listing.txt

```
">" pipes the output to the .txt files.

EDIT:
You should edit the history log so that it only includes the relevant commands.

---

