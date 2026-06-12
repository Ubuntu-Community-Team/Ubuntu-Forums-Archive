---
title: "How can I &quot;Automate&quot; Terminal Commands"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-26
Hello All !

I have following question:

I want to be able to automate some commands.

I want to be able to do the following:

1. cd /
2. mkdir fat32_files
3. mkdir ntfs_files
4. mkdir ntfs_os
5. cd /home/dimitris/Desktop
6. ... whatever...
7. ... whatever...
8. ... whatever...

I want to be able to run ALL the above commands, automatically (in "lazy" mode)...

So, I would lile to save them in a "auto.txt" file & then:

In a command prompt, just type:

        run auto.txt
or    sudo auto.txt

And ALL the above commands be performed automatically...

So basically, I ONLY type 1 command, but that is equivalent to HAVING typed all the above 8 commands individually!

Do not suggest me to use "chron", because I would only use such command ONLY once (e.g. whenever I formatted a Hard Drive & wanted some stuff be performed automatically).

Note:
The above procedure could help me automate a "Backup"/"Restore" procedure (e.g. using the "tar" procedure which is pretty long to type or remember).

Thanks.

---

### Post by xhie on 2006-02-26
put it all into a script

1) open your favoret text editor, gedit is always good

2) #!/bin/bash   goes on the first line

3) below that type all your stuff, just type it in there, one on each line if its
    easier to look at that way, and save it

4) chmod +x filename   this makes it executable

5) then just run your script wth ./filename  whenever you want, if you want to be abel to run it for anywhere stick it in /bin

Something like this:

```
#!/bin/bash

cd /
mkdir fat32_files
mkdir ntfs_files
mkdir ntfs_os
cd /home/dimitris/Desktop
 ... whatever...
 ... whatever...
... whatever...
```

---

### Post by Klaidas on 2006-02-26
I myself would create a simple script.

1. Create an empty document
2. Rename it to MyScript.sh
3. Open it, and insert this:

```
#!/bin/bash
cd /
mkdir something
more commands
```

Hope that helps

EDIT: Nevermind, xhie was faster than me :)

---

### Post by dvarsam on 2006-02-26
OK, I did what you suggested & it works only partially:

Let me explain:

I create this:

#!/bin/bash

cd /home/dimitris/Desktop

mkdir moly
mkdir tony

cd /

umount -a


First of all, the command "umount -a" is either ignored or NOT performed.

At the same time, you are suggesting to "create" a self-executable file....

I want to be able to do this from within the Terminal & NOT from a self-executable file, lying on the Desktop.

So, can I run the "auto.sh" from the terminal?

---

### Post by Klaidas on 2006-02-26
I think that some of those command require root access, so I think you should type (in terminal)
> sudo sh myscript
That's the command if I remeber correctly (I'm on windoze now)

---

### Post by dvarsam on 2006-02-26
... and let me also ADD this too!

If instead of making the directories on the Desktop I tell it to make them on the "File System" folder, the Folders are NOT made.

So it is useless. There MUST be another way on this...

I ONLY wanted to do it from the Terminal, because basically after I get the sudo rights (with "sudo -i), I could do anything.
That is why, I think it is better to do it from withing the Terminal & NOT from a ".sh" file on the Desktop....

Any Ideas?

---

### Post by xhie on 2006-02-26
Who told you to put the script on the desktop? 

yeah run it from the terminal, its a bash script for christs sakes, its ment to be run in a terminal. 

yeah you need to be sudo probably just run it with sudo filename, and your good to go.

---

### Post by dvarsam on 2006-02-26
At the same time I want to do this:

From the Terminal I want to go in the END of the "fstab" file, and:

1. Create a couple of "new" lines (just like pressing the "Enter" manually)

2. Insert: "/dev/sdb5    /fat32_files   vfat iocharset=utf8,umask=000  0  0"

3. Then Save changes to the "fstab" file & Exit it.

Is that possible?

How can I do this from the Terminal?

Thanks.

P.S.> Basically I want ot create an "auto.sh" file that I can use right after a Format 
         & automate everything to make my Ubuntu Up & running the Fastest 
         possible...

---

### Post by xhie on 2006-02-26
Isnt that just a one time thing? 

1) Open a terminal

2) be root if you need to be root 

3) be in the path where the file is located

4) gedit (or nano, vi, emacs, whatever editior you want) filename (fstab or whatever in your case) 

5) do your stuff

6) save and exit


Is how you edit files... or am I not understanding your question right?


Also...

to just stick some stuff on the end of a file:
Say your file is called file1, and in file2 you have the stuff you want to add to the end of file f1

cat file1 file2 

will do that for you

---

### Post by 5-HT on 2006-02-26
[QUOTE=dvarsam]At the same time I want to do this:

From the Terminal I want to go in the END of the "fstab" file, and:

1. Create a couple of "new" lines (just like pressing the "Enter" manually)

2. Insert: "/dev/sdb5    /fat32_files   vfat iocharset=utf8,umask=000  0  0"

3. Then Save changes to the "fstab" file & Exit it.

Is that possible?

How can I do this from the Terminal?

Thanks.

P.S.> Basically I want ot create an "auto.sh" file that I can use right after a Format 
         & automate everything to make my Ubuntu Up & running the Fastest 
         possible...[/QUOTE]


I agree with xhie in asking whether this is really something you'd like to do in a script, or if it's more of a once in a while or one time thing?
Personally, I wouldn't see the need of putting this in a script unless you're going to be needing to do it constantly...but if you want to here's how to do it.

If you're sure you want to do this in a script, just add something like this to your script:
```

#backing up fstab just in case anything goes wrong
cp /etc/fstab /etc/fstab.backup

#creating three carriage returns at end of fstab. Repeat this as many times as you like.
echo >> /etc/fstab
echo >> /etc/fstab
echo >> /etc/fstab


#appending new entry to fstab
echo "/dev/sdb5    /fat32_files   vfat iocharset=utf8,umask=000  0  0" >> /etc/fstab 
```

To do it manually, just do each step from the terminal (prefaced with 'sudo'), or even easier, just open up an editor and do it that way.

Note that to run this as a script, make sure you preface it with 'sudo' when executing.

Hope that helps.

---

