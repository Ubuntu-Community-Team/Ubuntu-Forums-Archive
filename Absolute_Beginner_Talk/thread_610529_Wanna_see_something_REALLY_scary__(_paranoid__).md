---
title: "Wanna see something REALLY scary ? ( paranoid ? )"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by WIREHEAD on 2007-11-12
Check this out :

Open a terminal type  " gksudo nautilus " without the quotes . Enter .

When Nautilus opens select " filesystem " open it with a double click , at the top of the window click " view " , and click on "show hidden files " .

Scroll down to " home " folder double click it and  you will see all users home folders except root . Double click on one of these folders , scroll down to the ".thumbnails " folder contained within . 

Doubleclick on the ".thumbnails" folder and then doubleclick on one of the folders contained in it " normal " would be a good start ,let me know what you see , it may take a goood long while for the contents to finish processing and show the contents if the system has been used much .

An absolutely pathetic waste of disk space is the mildest thing I have to say about this , If I were paranoid it might even anger me . 

Why are these here ?

---

### Post by TeaSwigger on 2007-11-12
Wouldn't call that scary; some of the things Windows caches, now that... ;)

Like in Windows and most OS with gui browsers that show thumbnails, Nautilus stores thumbnails as a helpful feature to speed browsing, and does so according to options you can change. You can opt to have no thumbnails saved, but that will require regenerating thumbnails each time, so browsing directories with a large number of files can be slow or sticky if your computer isn't very powerful. You can also delete the thumbnail caches as desired. Personally I like to keep thumbnail caches to a minimum to save disc space, but they don't worry me.

---

### Post by alienexplorers on 2007-11-12
I wrote a very basic script to keep my .thumbnail file clean so I don't waste disk space. It goes into each sub directory and deletes everything.

---

### Post by Maestro23 on 2007-11-12
> **alienexplorers said:**
> I wrote a very basic script to keep my .thumbnail file clean so I don't waste disk space. It goes into each sub directory and deletes everything.

That sounds very handy, could I get that script from you.  If you don't mind.:)

---

### Post by alienexplorers on 2007-11-12
Thumbnail cleanup script:

> #!/bin/sh
echo "starting cleanup"
sleep 2
echo
echo "deleting large thumbs"
sleep 2
cd /
cd /home/YOURNAME/.thumbnails/large
rm -fv *.*
rm -fv *
echo "large thumbs deleted"
sleep 2	
echo
echo "deleting normal thumbs"
sleep 2
cd /
cd /home/YOURNAME/.thumbnails/normal
rm -fv *.*
rm -fv *
echo "normal thumbs deleted"
sleep 2
echo
echo "deleting failed thumbs"
sleep 2
cd /
cd /home/YOURNAME/.thumbnails/fail/gnome-thumbnail-factory
rm -fv *.*
rm -fv *
echo "failed thumbs deleted"
sleep 2
echo
echo "thumbnail cleanup successfull"
sleep 2

Just change YOURNAME in file to your home directory name.

---

### Post by Maestro23 on 2007-11-12
> **alienexplorers said:**
> Thumbnail cleanup script:


Just change YOURNAME in file to your home directory name.

Cool.  Thanks alienE. :guitar:

---

### Post by kpkeerthi on 2007-11-12
```

find ~/.thumbnails -mtime 14  

```

The above command should display all the thumbnails that were created 14 days ago. If you wish to remove thede, then do:

```

find ~/.thumbnails -mtime 14  -exec rm '{}' ';'

```

This way you can get rid of the thumbails that were  not used in the last couple of weeks while keeping the rest.

---

### Post by _simon_ on 2007-11-12
Some of the stuff in my folder was months old, how totally random.

---

### Post by Steve1961 on 2007-11-12
Thanks for this script.  I never realised so much was cached.

---

### Post by ruibernardo on 2007-11-12
Nice and useful script, thanks. I've added it in my gnome-schedule (cron).

For those who don't want thumbnails to be created, disable them in Nautilus > Edit > Preferences > Preview and select "Never" instead of "Just local Files". No more thumbnails, not even on the Desktop - not the best solution for me.

I've found also another post about this. It is supposed to avoid the thumbnail creation (of other apps?) - [http://ubuntuforums.org/showpost.php?p=2080067&postcount=7](http://ubuntuforums.org/showpost.php?p=2080067&postcount=7), but didn't work for me in Gutsy.

---

### Post by Dripbagulhos on 2007-11-12
Yes, more than 15.000 itens on large folder... But aren't these thumbnails the responsible to show the contents of each of my data files? Well... I asked Gnome to show thumbnails, right? If I delete these thumbnails, I will have no preview of my data files, and as gnome wants to show me the preview, it will recreate then each time I open a folder wich is not cached, right?

I think I prefer to "waste" the space, than waste time waiting for gnome to re-create the previews.

Does anyone agree?

:-)

---

### Post by ruibernardo on 2007-11-12
I do, that's why I added the script to my cron with gnome-schedule.

---

### Post by paul.matthijsse on 2007-11-12
to check the size of your thumbnails dir, type in a terminal:
$ du -hs ~/.thumbnails

mine is 26 MB on a fresh install (3 days ago) of Gutsy. Nice OS btw... :-)

---

### Post by kvonb on 2007-11-12
-

---

### Post by Dripbagulhos on 2007-11-12
> **paul.matthijsse said:**
> to check the size of your thumbnails dir, type in a terminal:
$ du -hs ~/.thumbnails

mine is 26 MB on a fresh install (3 days ago) of Gutsy. Nice OS btw... :-)

Uau!!

Mine has 810 Mb!!

Does it never clear? I mean: if I delete a file, is the thumbnail deleted along? If not, I should reconsider and put a script on my cron to clean the thumbs older thant, for instance, 1 month...

---

### Post by Rinzwind on 2007-11-12
```
cd /
cd /home/YOURNAME/.thumbnails/large
rm -fv *.*
rm -fv *
```
Hmmm I don't like the cd / and rm here.
Someone not understanding scripting might just forget the YOURNAME and run it.
Would the rm -fv *.*  remove stuff from the root-dir. 


I would strongly suggest to use the 'find' command posted .

---

### Post by erfahren on 2007-11-12
yeah, I've came across that directory before. There were a bunch of pics of big-butted naked women and I have absolutely no idea how they got there! :-\"

I made a little script that I run periodically to clear out it and all those hidden backup files that end in the tilde (~) out of my home directory.
```

#!/bin/bash -x

find ~/ -name \*~ -exec rm {} \;
find ~/.thumbnails/normal/ -name \*.* -exec rm {} \;

```

I named it "cleartemp", set it to executable and put in the /home/<username>/bin directory I created. Then I just have to type "cleartemp" in the terminal to run it. for more info on that see: [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

---

### Post by MikeSz on 2007-11-12
Silly question I know - is a script like a windows batch file that you can just run from time to time or do you just paste the whole lot into terminal and let it go?  Never used a 'script' before....

---

### Post by erfahren on 2007-11-12
> **MikeSz said:**
> Silly question I know - is a script like a windows batch file that you can just run from time to time or do you just paste the whole lot into terminal and let it go?  Never used a 'script' before....
it's like a Windows batch file. I'm sure you've already have made and/or ran some in Ubuntu going by HowTos and the like without realizing it.
for more info on them see: [http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

---

### Post by MikeSz on 2007-11-12
Cheers - il have some fun with that!

---

### Post by steve.horsley on 2007-11-12
> **Dripbagulhos said:**
> Uau!!

Mine has 810 Mb!!

Does it never clear? I mean: if I delete a file, is the thumbnail deleted along? If not, I should reconsider and put a script on my cron to clean the thumbs older thant, for instance, 1 month...

In mine, the average size is around 10K per image. I reckon this is only 1-2% of the space the real images take up, so that's not a real problem. Of course, it might become an issue if I were looking at lots of transient images (I don't think it ages out old thumbnails by itself).

---

### Post by WIREHEAD on 2007-11-17
This actually inspired me to write my first working script .

Excellent link for shell script beginners :
[http://www.linuxcommand.org/writing_shell_scripts.php](http://www.linuxcommand.org/writing_shell_scripts.php)

  ****    THIS IS MY FIRST SCRIPT -- I PROVIDE THIS AS INFORMATION ONLY   ****
 ****  Worked for me , might make your machine burst into flames, or worse ****
****  Assume I am wrong just like every other wannabe linux newb on the net  ****

Save this in an editor to home directory as clean1  :

#!/bin/bash
#
# delete thumbnails 
#

echo " deleting thumb files "

cd

cd .thumbnails

cd large

rm *.png

ls

cd ..

cd normal

rm *.png

ls

echo " Space has been saved "

open a terminal type " chmod 755 ./clean1 " enter .
                       type " ./clean1 " enter

then look at your .thumbnails files and they will be empty .

I think there might have been a folder titled " failed " in the .thumbnails folder , could also add that .

<<<<<<<<<  PLEASE READ THE DISCLAIMER ABOVE ONE MORE TIME  >>>>>>>>>>

---

### Post by frank002 on 2007-11-17
Thanks for the script.

---

### Post by qpieus on 2007-11-17
What is the .thumbnail directory for anyway? I guess I don't see the point of saving all these pics.

Thanks to the original poster - I had seen this directory before but didn't realize how big it becomes (mine is 1 GB). I'm gonna use one of the scripts you guys have posted to clean that sucker out.

---

### Post by bluepowder7 on 2007-11-17
apparently i don't surf enough porn on this machine.  i have 13 items totaling only 90k.  it doesn't seem to show any icons or thumbnails from web surfing or pidgin.

i feel inadequate :(

---

### Post by SentientFluid on 2007-11-18
> **kpkeerthi said:**
> ```

[code]
find ~/.thumbnails -mtime 14  -exec rm '{}' ';'

```

This way you can get rid of the thumbails that were  not used in the last couple of weeks while keeping the rest.

Short and sweet, I like that. When I add that as a cron job, can I just use the command as you have it above or do I need to create a script to point the cron to?

---

### Post by kiepmad on 2007-11-18
I'm using this installation for more than a month now, and my thumbnail folder got 8,4 MB of size. What's the matter? What the hell are you using your PCs for? :P

---

### Post by Campingman on 2007-11-18
Absolutely astonishing and indeed very scary,  XP never did anything like this, did it?

---

### Post by nick_h on 2007-11-18
> find ~/.thumbnails -mtime 14  -exec rm '{}' ';'
Consider changing -mtime 14 to -atime +14 to select files accessed more than 14 days ago.  This will keep recently accessed files.  You need a + to indicate more than.

Also adding -name "*.png" and/or -type f will restrict the search to files of type "file" matching the pattern.

```
find ~/.thumbnails -type f -name "*.png" -atime +14  -exec rm '{}' ';'
```

The -size option may also be worth a look to just delete the biggest files.

---

### Post by qpieus on 2007-11-18
> **nick_h said:**
> 
```
find ~/.thumbnails -type f -name "*.png" -atime +14  -exec rm '{}' ';'
```

Nice changes, thanks. I used mtime +14 instead. atime didn't delete enough. This made my .thumbnails directory 40 MB instead of 1000 MB.

---

### Post by jordanmthomas on 2007-11-18
> **Campingman said:**
> Absolutely astonishing and indeed very scary,  XP never did anything like this, did it?

Yes, in every directory that has pictures, there is a file called Thumbs.db that contains thumbnails for the pictures in the directory.

---

### Post by stimpack on 2007-11-19
Fan-bloody-tastic, my entire encryption scheme compromised in one silly directory. If my gf new about .thumbnails I'd be in big trouble.

---

### Post by dimeotane on 2007-11-29
a really easy solution: 

sudo apt-get install gnome-schedule  (perhaps it is included in gutsy by default?)

go to applications-->system tools-->schedule  

make a new entry: go to the basic tab:  
choose recurrence 'every day' enter this command, and make sure 'no output' is not selected
rm ~/.thumbnails/normal/*.* 

every day your thumbnails folder will be wiped. set it and forget it.:guitar:

---

### Post by WIREHEAD on 2007-12-08
dimeotane,

THANKS for that !
This simplifies alot of things I was attempting to solve with scripts ( attempting would be the key word ) .

I'll be tinkering with this schedule program for a while ... 

Very cool !

---

### Post by ruibernardo on 2007-12-08
Nice, isn't it? :)

---

### Post by Biggus on 2007-12-08
Hmm that is pretty far out.

I had a years worth of porno thumbnails in thar.

---

### Post by Gadren on 2007-12-08
Heh... *nervous laughter*
This is interesting.

But not a problem any more; I already had a couple scripts to automatically mount and unmount some truecrypt partitions upon password confirmation, and my unmount script now has commands to remove all images from .thumbnails.  Sure, it's not the best way to do it, since it would also remove, er, non-sensitive images, but it'll do for now.

Thanks for pointing this out!

---

