---
title: "Please help debug a bash script!!"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-05-27
So I wrote a bash script to help anyone who recovers Data from corrupted hard drives using PhotoRec, and I need help fixing a problem that I think just needs a second perspective. As some background, PhotoRec will save any recovered files to recup_dir.* in your home directory (in my last recovery it made 139 recup_dir.* directories). This script is to help make sorting through those files easier, but I keep getting errors about an unexpected end of document, and I feel like it is just a stupid mistake that I am missing that is causing it. Here is the script:

```
#!/bin/bash

#This is a script to move files recovered by PhotoRec into one folder, and should be run from your home

# Folder by typing sudo sh prorganize.sh into your terminal. If you have any questions, please write to #wishingforayer@gmail.com

sudo chmod -v 777 recup_dir.*
for i in recup_dir.*/*; do sudo chmod -v 777 $i; done
mkdir -v prsaves

cd prsaves

mkdir -v images

mkdir -v video

mkdir -v text

mkdir -v docs

mkdir -v music

mkdir -v html

mkdir -v everythingelse

cd ..
sudo chmod -r 777 prsaves

echo "Now moving images"

#This command will scan all of your recup_dir.* folders for image files, and move them to your

# prsaves/images/ folder. To add a filetype just add *.filetype after *.psd

for i in recup_dir.*/*.jpg *.jpeg *.gif *.png *.psd; do mv -vf $i prsaves/images/; done

echo "Now moving video"

for i in recup_dir.*/*.mpeg *.avi *.mov *.mpg *.xvid; do mv -vf $i prsaves/video/; done

echo "now moving text files"

for i in recup_dir.*/*.txt; do mv -vf $i prsaves/text/; done

echo "Now moving documents"

for i in recup_dir.*/*.doc *.odt *.ods *.odp *.odg *.odf *.ppt; do mv -vf $i prsaves/docs/; done

echo "Now moving music"

for i in recup_dir.*/*.mp3 *.ogg *.wav; do mv -vf $i prsaves/music/; done

echo "Now movint HTML files"

for i in recup_dir.*/*.html; do mv -vf $i prsaves/html/; done

echo "Now moving whatever is left"

for i in recup_dir.*/*; do mv -vf $i prsaves/everythingelse/; done

rmdir recup_dir.*

echo "Have a great day!"

done
exit 0

```

Thank you all so much for your help, and I hope someone is able to help!!

---

### Post by pmg on 2007-05-28
I haven't used the PhotoRec tool, but from a very quick look at your script:
[LIST]
[*]Are you sure you want to "sudo chmod 777" the files?  That will make them readable and writable by any userid.  If you're the only user on your system it may not matter, but if this is something you are planning on sharing you should think about that.  The command "chmod 777" also sets the execute bit on the files.  You really don't want to set the execute bit on non-executable files.

[*]In your **for** lines like "for i in recup_dir.*/*.jpg *.jpeg *.gif *.png ...", I think you mean "for i in recup_dir.*/*.jpg *recup_dir.*/.jpeg *recup_dir.*/*.gif *recup_dir.*/*.png ....", or more simply "for i in recup_dir.*/*.{jpg,jpeg,gif,png} ..."

[*]Are you sure you want to use the **-f** flag on the **mv** commands?  If two files happen to have the same names from different directories, you're going to have the last one overlay any earlier files.

[*]What is the **done** at the very end of the script for?  I didn't see any **do** for it to match up with.

[*]Putting the command "set -o verbose" somewhere near the beginning of your script, or someplace before where things go bad, may give you a better idea what's happening.
[/LIST]

---

### Post by brennydoogles on 2007-05-28
> **pmg said:**
> I haven't used the PhotoRec tool, but from a very quick look at your script:
[LIST]
[*]Are you sure you want to "sudo chmod 777" the files?  That will make them readable and writable by any userid.  If you're the only user on your system it may not matter, but if this is something you are planning on sharing you should think about that.  The command "chmod 777" also sets the execute bit on the files.  You really don't want to set the execute bit on non-executable files.

[*]In your **for** lines like "for i in recup_dir.*/*.jpg *.jpeg *.gif *.png ...", I think you mean "for i in recup_dir.*/*.jpg *recup_dir.*/.jpeg *recup_dir.*/*.gif *recup_dir.*/*.png ....", or more simply "for i in recup_dir.*/*.{jpg,jpeg,gif,png} ..."

[*]Are you sure you want to use the **-f** flag on the **mv** commands?  If two files happen to have the same names from different directories, you're going to have the last one overlay any earlier files.

[*]What is the **done** at the very end of the script for?  I didn't see any **do** for it to match up with.

[*]Putting the command "set -o verbose" somewhere near the beginning of your script, or someplace before where things go bad, may give you a better idea what's happening.
[/LIST]

well, a few quick things...

The reason I have the chmod set to 777 is that I was designing this for multi user systems (which is the only place I have ever used PhotoRec). Because PhotoRec needs to be run as root, the Chmod is necessary, but should I use 755 instead of 777 (I can't remember offhand how to figure out what i need... i just know that 777 is full access to all users)

For the filetype grouping, I know that how I have it in the script works while typing directly into the terminal, but I will try some of your suggestions to see if maybe that will help.

As for the **-f** flag on the mv command, I actually had a very good reason for using that with my computers. As per advice from a few tutorials for linux noobs, I have set up an alias on all of my linux boxes that effectively changed my mv command to mv -i  (meaning that any script user would have to manually approve the move of several thousand files... and that would suck) . Because files saved with PhotoRec are named using the letter f and long strings of numbers (each of which is unique) I was not afraid of overwriting anything, since all of the directories used in the script are created by it. I know that others may have read that advice as well, so i figured the -f flag was safe to use in this instance.

And lastly, the **done** at the end of the script was me attempting to figure out why I keep getting the error from my first post. I will add the set -o verbose next time i run to see what I can find. Thanks for your help!!

---

### Post by brennydoogles on 2007-05-28
ok, here is the output of ```
set -o verbose
```

```

brendon@desktop:~$ sudo sh prorganize.sh
#sudo chmod -v 777 recup_dir.*
#for i in recup_dir.*/*; do sudo chmod -v 777 $i; done
mkdir -v prsaves
mkdir: cannot create directory `prsaves\r': File exists
cd prsaves
mkdir -v images
mkdir: cannot create directory `images\r': File exists
mkdir -v video
mkdir: cannot create directory `video\r': File exists
mkdir -v text
mkdir: cannot create directory `text\r': File exists
mkdir -v docs
mkdir: cannot create directory `docs\r': File exists
mkdir -v music
mkdir: cannot create directory `music\r': File exists
mkdir -v html
mkdir: cannot create directory `html\r': File exists
mkdir -v everythingelse
mkdir: cannot create directory `everythingelse\r': File exists
cd ..
sudo chmod 777 prsaves
echo "Now moving images"
Now moving images
#This command will scan all of your recup_dir.* folders for image files, and move them to your
# prsaves/images/ folder. To add a filetype just add *.filetype after *.psd
for i in recup_dir.*/*.jpg *.jpeg *.gif *.png *.psd; do mv -vf $i prsaves/images/; done
echo "Now moving video"
for i in recup_dir.*/*.mpeg *.avi *.mov *.mpg *.xvid; do mv -vf $i prsaves/video/; done
echo "now moving text files"
for i in recup_dir.*/*.txt; do mv -vf $i prsaves/text/; done
echo "Now moving documents"
for i in recup_dir.*/*.doc *.odt *.ods *.odp *.odg *.odf *.ppt; do mv -vf $i prsaves/docs/; done
echo "Now moving music"
for i in recup_dir.*/*.mp3 *.ogg *.wav; do mv -vf $i prsaves/music/; done
echo "Now movint HTML files"
for i in recup_dir.*/*.html; do mv -vf $i prsaves/html/; done
echo "Now moving whatever is left"
for i in recup_dir.*/*; do mv -vf $i prsaves/everythingelse/; done
rmdir recup_dir.*
echo "Have a great day!"
done
exit 0
prorganize.sh: 38: Syntax error: end of file unexpected (expecting "done")
brendon@desktop:~$ 


```

Note: I commented out the chmod, because the files and folders already have the right permissions.

---

### Post by pmg on 2007-05-28
re: chmod.  Glad you were able to remove that.  A little more help on chmod and the meaning of the mode bits is at [http://catcode.com/teachmod/chmod_cmd.html]("http://catcode.com/teachmod/chmod_cmd.html")

re: filetype grouping.  After a second look, you don't need the **for** loops at all.  **mv** can move multiple files at once, so you could just use something like:  ```
mv recup_dir.*/*.{jpg,jpeg,gif,png,psd} prsaves/images/
```  [UPDATE: If there is nothing at all to move, you'll get an error, but you could get around that by creating a dummy file to move so you know there's always at last one (and then cleaning it up after the mv.)]

re: -f in mv. That is an alias setup for an interactive shell.  I really don't use bash much myself, but I don't think that's set in a script.  If it is, you could remove the alias in your script with **unalias**, or you could always call **mv** by absolute path to bypass the alias (i.e. /bin/mv.)

re: **done** at end.  That does look strange.  When I run your script I don't get that error at the end.  The 38 in the error message indicates the line where the error was detected.  I wonder if you have something in your ~/.bash_profile or ~/.bashrc (or another file they reference) that is causing the problem.  Try writing a script with nothing but:
```
#!/bin/bash
echo done.
```
and see if you get that message.

---

### Post by brennydoogles on 2007-05-29
> **pmg said:**
> re: chmod.  Glad you were able to remove that.  A little more help on chmod and the meaning of the mode bits is at [http://catcode.com/teachmod/chmod_cmd.html]("http://catcode.com/teachmod/chmod_cmd.html")

re: filetype grouping.  After a second look, you don't need the **for** loops at all.  **mv** can move multiple files at once, so you could just use something like:  ```
mv recup_dir.*/*.{jpg,jpeg,gif,png,psd} prsaves/images/
```  [UPDATE: If there is nothing at all to move, you'll get an error, but you could get around that by creating a dummy file to move so you know there's always at last one (and then cleaning it up after the mv.)]

re: -f in mv. That is an alias setup for an interactive shell.  I really don't use bash much myself, but I don't think that's set in a script.  If it is, you could remove the alias in your script with **unalias**, or you could always call **mv** by absolute path to bypass the alias (i.e. /bin/mv.)

re: **done** at end.  That does look strange.  When I run your script I don't get that error at the end.  The 38 in the error message indicates the line where the error was detected.  I wonder if you have something in your ~/.bash_profile or ~/.bashrc (or another file they reference) that is causing the problem.  Try writing a script with nothing but:
```
#!/bin/bash
echo done.
```
and see if you get that message.

The reason the for loops are there is for the sheer number of arguments. mv will allow multiple arguments, but not infinite arguments. In this case any one of those commands can have massive amounts of arguments ( my last recovery had 20,000 .txt files) I will continue debugging and see what I can come up with.

---

### Post by brennydoogles on 2007-05-30
bump

---

### Post by pmg on 2007-05-31
> **brennydoogles said:**
> The reason the for loops are there is for the sheer number of arguments. mv will allow multiple arguments, but not infinite arguments. In this case any one of those commands can have massive amounts of arguments ( my last recovery had 20,000 .txt files) I will continue debugging and see what I can come up with.
Yeah, the limit is around 131,000 bytes of command arguments, minus whatever is used by environment variables.  If you need to operate on longer argument lists than that it's time to look at the **xargs **command.  You could use something like:
```
find recup_dir* -type f | grep -e '\.jpg$' -e '\.jpeg$' -e '\.gif$' | xargs -t -r mv --target-directory=prsaves/images/
```
or
```
find recup_dir* -type f \( -path '*.jpg' -o -path '*.jpeg' -o -path '*.gif' \) | xargs -t -r mv --target-directory=prsaves/images/
```
That is admittedly getting as complicated as the for loops, but it would execute faster.  Either of the pipeline commands also have the advantage that the shell process doesn't have to buffer all the file names that need to be moved, so they could handle more files then the shell **for** loop approach.

Did you try the very simple shell script to see if you still get the error  message at the end?

---

