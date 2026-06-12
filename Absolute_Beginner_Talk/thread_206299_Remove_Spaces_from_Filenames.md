---
title: "Remove Spaces from Filenames"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-06-29
Is there a bash command, or some script that anyone knows of that can rename all files in a directory and remove the spaces?

---

### Post by 23meg on 2006-06-29
With a google search I found these:

[http://www.linuxquestions.org/questions/showthread.php?t=265933](http://www.linuxquestions.org/questions/showthread.php?t=265933)
[http://www.linuxquestions.org/questions/showthread.php?t=207632](http://www.linuxquestions.org/questions/showthread.php?t=207632)

Also look here for all your script needs: [http://www.shelldorado.com](http://www.shelldorado.com)

---

### Post by DSn0wMan on 2006-06-29
Thanks 23meg,

I will post my script when I get it working.

---

### Post by uzi09 on 2006-06-29
i think i recall seeing something by the name of **krename** for this.

---

### Post by bikeboy on 2006-06-29
I got some help a while ago when I wanted to remove the %20 (put there instead of a space) from lecture notes I downloaded off my uni intranet. It's not quite what you want but it might give you some guidence.

> 
#/bin/bash
for name in *%20*; do
    mv "$name" "${name//\%20/ }"
done


---

### Post by DSn0wMan on 2006-06-29
This is what worked for me ```
#!/bin/bash
IFS='
'
j=`find $1 -printf "%d\n" | sort -u | tail -n 1` 
echo "Max dir depth:" $j
for (( i=0; i<=j ; i++ ))
do
  for name in `find -mindepth $i -maxdepth $i -iname "* *" -printf "%p\n"`
  do
    newname=`echo "$name" | tr " " "_"`
    echo "$name" "$newname"
    mv "$name" "$newname"
  done
done
```This will replace spaces with underscores recursively in the directory you run it in

---

### Post by mostwanted on 2007-10-03
> **DSn0wMan said:**
> This is what worked for me ```
#!/bin/bash
IFS='
'
j=`find $1 -printf "%d\n" | sort -u | tail -n 1` 
echo "Max dir depth:" $j
for (( i=0; i<=j ; i++ ))
do
  for name in `find -mindepth $i -maxdepth $i -iname "* *" -printf "%p\n"`
  do
    newname=`echo "$name" | tr " " "_"`
    echo "$name" "$newname"
    mv "$name" "$newname"
  done
done
```This will replace spaces with underscores recursively in the directory you run it in

Thanks a lot. I really needed to replace some characters in my music collection and this did the trick! :)

---

### Post by Oki on 2007-10-03
I use the file manager Thoggen and the renamer plugin(all from Synaptic). It works very well, also for remvoing spaces.

---

### Post by bodhi.zazen on 2007-10-03
> **DSn0wMan said:**
> Is there a bash command, or some script that anyone knows of that can rename all files in a directory and remove the spaces?

cool scripts 8)

You can also use rename :

```
rename -v 's/\ /\_/g' *
```

The -v flag is verbose :

*Will rename files and directories in current directory only

> bodhi@VirtualUbuntu:~$ ls -l | grep test
-rw-r--r-- 1 bodhi bodhi         0 2007-10-03 16:51 hi mom test
-rw-r--r-- 1 bodhi bodhi         0 2007-10-03 16:51 test 1
-rw-r--r-- 1 bodhi bodhi         0 2007-10-03 16:51 test 2
-rw-r--r-- 1 bodhi bodhi         0 2007-10-03 16:51 test 3
[color=red]d[/color]rwxr-xr-x 2 bodhi bodhi      4096 2007-10-03 16:49 test ing

bodhi@VirtualUbuntu:~$ [color=blue]rename -v 's/\ /\_/g' *[/color]
hi mom renamed as hi_mom
hi mom test renamed as hi_mom_test
test 1 renamed as test_1
test 2 renamed as test_2
test 3 renamed as test_3
test ing renamed as test_ing

bodhi@VirtualUbuntu:~$ ls -l | grep test
-rw-r--r-- 1 bodhi bodhi         0 2007-10-03 16:51 [color=blue]hi_mom_test[/color]
-rw-r--r-- 1 bodhi bodhi         0 2007-10-03 16:51 [color=blue]test_1[/color]
-rw-r--r-- 1 bodhi bodhi         0 2007-10-03 16:51 [color=blue]test_2[/color]
-rw-r--r-- 1 bodhi bodhi         0 2007-10-03 16:51 [color=blue]test_3[/color]
[color=red]d[/color]rwxr-xr-x 2 bodhi bodhi      4096 2007-10-03 16:51 [color=blue]test_ing[/color]

bodhi@VirtualUbuntu:~$  

---

### Post by ncappel1 on 2007-10-07
Yay, thanks for the thread, this is exactly what I needed. 

bodi.zazan, I knew there had to be a way to do it with the rename command, but I have a hard time understanding perl expressions. between the man pages and what I find on the internet I don't understand what the symbols mean, i just enter the commands and hope it works :( 

edit:

does anyone have any tips on removing whitespaces recursivly for a directory? If not I have to run the command into 50+ folders by hand...there must be a better way? I'm trying to play with grep -r and piping it into rename, but it hasn't been working so far...

n

---

### Post by ncappel1 on 2007-10-07
Don't mean to respond to my own posts, but after a little more persistance, I found a solution to my problem. I used two commands to edit the files filenames:

to remove spaces from the file names

```
find -type f -exec rename 'y/\ /\_/' {}  \;
``` 
(I had to remove the quotes for it to work)

the the following to translate upper case to lower case:
```
find -type f -exec rename rename &#8217;y/A-Z/a-z/&#8217; {} \;
```

still don't understand where the "y" comes from in the perl expression. the sites I found on google describe the translation as "tr." At least it works!

---

### Post by kaiju on 2008-01-31
just needed this script, too.
thank you very much :)

---

### Post by pmorton on 2008-03-22
Use a Nautilus script.

Copy the following script to a file called (say) "scorespaces":-

```
#!/bin/bash
find | while read FN;do mv "$FN" "`echo $FN | sed -e 's/ /_/g'`";done
```

make the file executable:-

```
chmod +x scorespaces
```

and move  it into the nautilus scripts directory of your home folder:-
```

mv ./scorespaces ~/.gnome2/nautilus-scripts
```

start nautilus; go to the folder in which the files you wish to change are located; right click, select "Scripts" and run the script "scorespaces". All files in the directory tree below the one you are in are renamed with underscores replacing spaces. The script, run in a terminal, will of course do the same job.

(with thanks to eileen lu [http://www.gtk-apps.org](http://www.gtk-apps.org))

---

### Post by cdannenberg on 2008-06-13
Hi, I'm new to Linux, Ubuntu and the forum...  I need to carry out a similar function, but with an added problem.  I've set up a server for images to be stored on, and since quality is an issue they've asked that users send in raw files.  I've set a directory up so these raw files get converted into tif files automatically, but this fails if there are spaces in the file names.  I understand crontab and how to tell a script when to run, but how can I change one of the scripts above to focus on and convert files in a specific directory?

---

### Post by kaiju on 2008-06-15
> **cdannenberg said:**
> [...]how can I change one of the scripts above to focus on and convert files in a specific directory?

just in case you didn't figure this one out already, probably the most obvious way would be to change directory to where the files are, before executing the command. like `cd /wherever/the/dir/is && whatever-command`.

---

