---
title: "How to change permissions recursively to folders only"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by dfreer on 2007-06-07
Hi all,

  Basically I want to change the permissions of my music collection (With Artists folders, then album folders in those folders, followed by the actual music) so that everyone can read my music. All of the folders should be 755, or rwxr-xr-x, and all of the files (important) should be 644 or rw-r--r--. Using a sudo chmod 755 -Rv * won't work, because then all of my files will be changed to the wrong permissions. :(

How can I change the permissions of the folders only without changing the permissions of the files, and without having to dive into each and every artists folder manually? 

I figure I probably need to use a bash script, but I don't know enough about bash to make it cd in and out of each directory.

---

### Post by meatpan on 2007-06-07
The find command has some useful options for selecting specific types of files.  Also, you have the ability to execute a command on each file that is found. 

Try this command:
find . -type d -exec chmod 755 {} \;

Here is how it works.  The '.' after find is a location to start the search.  In this example you didnt give the name of a directory, so I'm assuming that you will run the command at the top directory level of your music files.  You can change this to somthing else, such as ~/music/albums, and find will start at that directory.  The '-type d' portion of the command instructs find to only select files that are of a directory type.  The find manpage has a list of other types of files that are possible as well.  Finally, '-exec chmod 755 {} \;' will cause chmod 755 <found-file> to be executed. Note, the braces {}, are substitued for the file name at run-time.  You must terminate find with ';', so in a shell it will need to be escaped, hence the backslash.

The find command is powerful, and can be very helpful.  Since it has so many options and uses, it takes a little bit of practice.

---

### Post by steeleyuk on 2007-06-07
This method is by no means perfect (I'm no good with these permission things) but couldnt you do:

chmod -R 755 * (to change all files and folders)

then do

chmod -R 644 *.mp3 (to change MP3 files only)

Edit: definitely use meatpan's method :)

---

### Post by dfreer on 2007-06-07
> **meatpan said:**
> The find command has some useful options for selecting specific types of files.  Also, you have the ability to execute a command on each file that is found. 

Try this command:
find . -type d -exec chmod 755 {} \;

Here is how it works.  The '.' after find is a location to start the search.  In this example you didnt give the name of a directory, so I'm assuming that you will run the command at the top directory level of your music files.  You can change this to somthing else, such as ~/music/albums, and find will start at that directory.  The '-type d' portion of the command instructs find to only select files that are of a directory type.  The find manpage has a list of other types of files that are possible as well.  Finally, '-exec chmod 755 {} \;' will cause chmod 755 <found-file> to be executed. Note, the braces {}, are substitued for the file name at run-time.  You must terminate find with ';', so in a shell it will need to be escaped, hence the backslash.

The find command is powerful, and can be very helpful.  Since it has so many options and uses, it takes a little bit of practice.

That looks great, I'll give find a lookover here really quick and let you guys know the results, thanks!

@steeleyuk
That would also probably work, although I would have to run it for *.jpg *.png *.mp3 *.wma *.m4p and a few others, I was thinking about doing that command myself, but I figured there was probably a better way (it seems you think so too ;) ). thanks for posting!

---

### Post by trak87 on 2007-06-07
The 'find' method mentioned above is probably the way to go, however this will do the trick:

```
cd <your_start_directory>
sudo chmod -R 644 * ; sudo chmod -R ugo+X *
```

You can run multiple commands by separating each command with a semi-colon. The first command changes everything to 644 permissions, but this isn't right for directories. So the second command sets all the directories to 755. The 'X' makes it deal with directories only. This is a bit of a kludge and is why I say the 'find -exec' method is probably better. However, I've been using this method for a long time with excellent results.

I use 'sudo' in my example on the off chance that there's a file floating around with root ownership. BTW, if you want to change ownership, use "chown -R owner:owner *"

Caveat for newbies: Be careful where you run the above code. For example, you can really screw up your system running it at the root directory.

---

### Post by steeleyuk on 2007-06-07
> That would also probably work, although I would have to run it for *.jpg *.png *.mp3 *.wma *.m4p and a few others, I was thinking about doing that command myself, but I figured there was probably a better way (it seems you think so too  ). thanks for posting! 

You could do:

chmod -R 644 *.*

if you felt lazy (or efficient) :)

---

### Post by dfreer on 2007-06-07
worked perfectly!
here's the command I used:
find /media/hdc1/media/music/ -type d -exec chmod 755 {} \;
and all of the directories in my music folder were changed correctly. It looks like find is incredibly useful, it can even descend a specified number of directories. Definitely gonna have to learn how to use this tool, thanks for suggesting it meatpan!

---

### Post by Inxsible on 2007-06-07
> **trak87 said:**
> 
```
cd <your_start_directory>
sudo chmod -R 644 * ; sudo chmod -R uga+X *
```


Shouldn't that be ugo as in user group others --- instead of uga ? I could be wrong however.

---

### Post by dfreer on 2007-06-07
> **steeleyuk said:**
> You could do:

chmod -R 644 *.*

if you felt lazy (or efficient) :)

.... I'm a tool lol. that's probably the simplest command of them all. However, find is also going to be incredibly useful I think.

> **trak87 said:**
> The 'find' method mentioned above is probably the way to go, however this will do the trick:

```
cd <your_start_directory>
sudo chmod -R 644 * ; sudo chmod -R uga+X *
```

Shouldn't this be like this?

```
sudo chmod -R 644 *; sudo chmod -R **755** uga+X *
```
Not quite sure where you are changing the permission in the last bit of code.

---

### Post by trak87 on 2007-06-07
> **dfreer said:**
> Shouldn't this be like this?

```
sudo chmod -R 644 *; sudo chmod -R **755** ugo+X *
```
Not quite sure where you are changing the permission in the last bit of code.

I don't think so. Using 755 is the octal form of setting permissions while +X is the textual form but they are different. The +X tells the command to **only** set directories, not files. 755 won't ignore files like +X does, so you need to use ugo+X

---

### Post by trak87 on 2007-06-07
I just tried the find method and it works pretty well. I googled and found others using this method so I believe the following is correct. 

To fix permissions in a music directory, this will work:


```
cd <your_music_directory>
find . -type d -exec chmod 755 {} \;
find . -type f -exec chmod 644 {} \;
```

---

### Post by arron on 2007-06-07
Nice simple script!  Can anyone recommend a good shell command or script howto to pick up some of these cool ideas for what can be done at the prompt?

---

### Post by trak87 on 2007-06-07
> **Inxsible said:**
> Shouldn't that be ugo as in user group others --- instead of uga ? I could be wrong however.

Yes, I think you are correct. 'ugo' is equivalent to just 'a'. I'll correct my previous post.

---

### Post by dfreer on 2007-06-07
> **trak87 said:**
> I just tried the find method and it works pretty well. I googled and found others using this method so I believe the following is correct. 

To fix permissions in a music directory, this will work:


```
cd <your_music_directory>
find . -type d -exec chmod 755 {} \;
find . -type f -exec chmod 644 {} \;
```

Can you specify specific files this way, like let's say to remove the annoying Thumbs.db files windows leaves in every directory:

```
find . -type f -exec rm Thumbs.db {} \;
```
or even better both the Thumbs.db and the ehthumbs.db
```
find . -type f -exec rm *.db {} \;
```
These codes should work shouldn't they (before I go try it on my media database)?

---

### Post by trak87 on 2007-06-07
I think what you have above will work, but consider the following:

```
find . -name *.db -type f -exec echo {} \;
```

Note that you specify what you are trying to find with "-name" and then it runs a command (echo in this case) directly after -exec. Your example above finds all files and removes *.db from ALL files. But there's no point in sending ALL the files to the "rm *.db" command.  Run the following and you'll see what I mean:

#Finds everything
find . -type f -print

verses this better example

#Finds only what you are looking for:
find . -name *.db -type f -print

change -print to -exec <command> {} \; to run a command on what is found.

And for testing I always insert "echo" for the exec command and test that. And only if I'm sure it's working (and maybe after a real live test on non-essential files) would I replace echo with a "rm" command.

So run this:
```
find . -name *.db -type f -exec echo rm {} \;
```

And if the results looks correct, remove the "echo" keyword and run it again. It will then delete all the *.db files it finds.

I hope that makes sense. I learned something trying to 'splain it.

---

### Post by dfreer on 2007-06-07
> **trak87 said:**
> I think what you have above will work, but consider the following:

```
find . -name *.db -type f -exec echo {} \;
```

Note that you specify what you are trying to find with "-name" and then it runs a command (echo in this case) directly after -exec. Your example above finds all files and removes *.db from ALL files. But there's no point in sending ALL the files to the "rm *.db" command.  Run the following and you'll see what I mean:

#Finds everything
find . -type f -print

verses this better example

#Finds only what you are looking for:
find . -name *.db -type f -print

change -print to -exec <command> {} \; to run a command on what is found.

And for testing I always insert "echo" for the exec command and test that. And only if I'm sure it's working (and maybe after a real live test on non-essential files) would I replace echo with a "rm" command.

So run this:
```
find . -name *.db -type f -exec echo rm {} \;
```

And if the results looks correct, remove the "echo" keyword and run it again. It will then delete all the *.db files it finds.

I hope that makes sense. I learned something trying to 'splain it.

Made perfect sense, and the echo command is VERY useful to use to test what would be deleted. I didn't run your command, per se, I simply used the verbose switch on rm to output what was deleted. so
```

find . -name *.db -type f -exec echo {} \;
find . -name *.db -type f -exec rm -v {} \;

```

works great! thanks again to everyone!

---

### Post by trak87 on 2007-06-08
Something occurred to me last night about find -ecec commands. What about whitespace in filenames?! My examples do not account for this. Any ideas?

---

### Post by dfreer on 2007-06-08
hmm I'm thinking you can just escape it, lemme check here....

Yep. On my hard drive I have a photo located:
~/pictures/Nicky's Birthday Party/My Pictures0001.jpg

Doing this command will correctly find and display the file:
```
$ find . -name *.jpg -type f -exec echo {} \;
.....
./pictures/Nicky's Birthday Party/My Pictures0001.jpg
.....
```
As well as this one, looking specifically for the filename with an escaped whitespace in the filename:
```
$ find . -name My\ Pictures0001.jpg -type f -exec echo {} \;
./pictures/Nicky's Birthday Party/My Pictures0001.jpg
```

Is that what you meant?

---

### Post by trak87 on 2007-06-08
I may be misunderstanding how find works, but this is more what I meant:

$ find . -name *.jpg -type f -exec rm {} \;

I believe would result in:

rm ./My Pictures/Nicky's Birthday Party/My Pictures0001.jpg

But what about the spaces?

It needs to be more like this:

rm "./pictures/Nicky's Birthday Party/My Pictures0001.jpg"

So would you do something like this?:

'{}' or \"{}\"

---

### Post by dfreer on 2007-06-08
No need. Just ran a test, here's the results:
```
mkdir ~/test
mkdir ~/test/my\ pics/
touch ~/test/my\ pics/my\ picture\ 001.jpg
cd ~/test/

find . -name *.jpg -type f -exec echo {} \;
./my pics/my picture 001.jpg
$ find . -name *.jpg -type f -exec rm **-iv** {} \;
rm: remove regular empty file **`./my pics/my picture 001.jpg'**? y
removed `./my pics/my picture 001.jpg'
```

Note the -iv argument. -i stands for interactive, to prompt the user before it deletes files. Just in case...

EDIT: Also, it seems to append a ` and a ' to the beginning and end of the file

---

### Post by trak87 on 2007-06-08
Excellent!

---

