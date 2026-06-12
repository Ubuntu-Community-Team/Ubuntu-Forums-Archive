---
title: "Unzipping a .rar file"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Qwerty_ on 2006-10-04
How do i unzip a .rar file on linux? Can it be done?

---

### Post by bluefrog on 2006-10-04
you have to install unrar programs first.

should find them in synaptic once you have enabled universe and/or multiverse repository (in synaptic, settings/repositories)

James

---

### Post by Qwerty_ on 2006-10-04
I installed unrar from Synaptic only place i could find it and when i double click it Archive manager runs and says Archive type not supported.

---

### Post by ciscosurfer on 2006-10-04
Right-click > Extract Here

---

### Post by pay on 2006-10-04
sudo aptitude install rar
then right click the .rar and press extract.

---

### Post by Qwerty_ on 2006-10-04
> **pay said:**
> sudo aptitude install rar
then right click the .rar and press extract.

OK i did that but i got

sudomike@123456:~$ sudo apt-get install rar
Password:
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
mike@123456:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
mike@123456:~$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate
mike@123456:~$

It appears that i have the universe and multiverse in my sources.

---

### Post by bluefrog on 2006-10-04
is there another occurence of unrar by chance (unrar-unfree?)

---

### Post by Qwerty_ on 2006-10-04
Yeah thats what i installed.

---

### Post by Ben Sprinkle on 2006-10-04
[http://rarlabs.com](http://rarlabs.com)
Download the linux version and extract, go in your terminal and type this:
```

'/home/$USER/Desktop/rar/unrar' e rarfile.rar

```
e Means extract in current directory. :)

---

### Post by jonathan21 on 2006-10-04
open synatic package manager.open settings.then open repositories make sure all items are ticked.click on okay.open terminal type

sudo apt-get update

then sudo apt-get install rar

---

### Post by dannyboy79 on 2006-10-04
i used automatix and my right click option in nautilus works great, an option appears that says, extract here. or you could always do sudo aptitude install unp. then at the command line you would type sudo unp /home/blah blah/movie.r00 if it's part of a rar set or movie.rar if it's just one rar file. i tried unp after the normal archive manager wasn't working but it turned out the one of the rar files of the rar set was named differently and once I named it correctly it worked fine. automatix was the bomb, i got tons of stuff installed with the snap of a finger. sure i didn't learn how to install stuff one by one but I am learning by installing Opera from source as well as bittornado 0.3.15 etc etc.

---

### Post by Ben Sprinkle on 2006-10-04
You guys could try my way also, it's the way I use rar files.
It may require using the terminal but it's still easier if your a noob and don't know how to install things. :)

---

### Post by got_nix on 2006-10-04
if you do intend to use rar type rar --help to get the commands i think you need the -e switch to extract it.

---

### Post by Qwerty_ on 2006-10-04
I extracted the rar programme got all the files but not sure how to install them. Do i install them?

---

### Post by Ben Sprinkle on 2006-10-04
Are you referring to my way?
If so it's already installed...well sort of. It does not require installing.
To use just drag the rar folder to your desktop, open a terminal and type this:
```

cd Desktop
'rarfolder/unrar' e 'path-to=rarfile.rar'

```
Understand?

---

### Post by Qwerty_ on 2006-10-04
Yeah i am referring to your way but i am sorry i dont understand what you mean.

---

### Post by Ben Sprinkle on 2006-10-04
Alright then seeing as your new I will break it down. :)
This will be the most easiest way to do it.

1. Download WinRar from [http://rarlabs.com](http://rarlabs.com) -Linux Version
2. Extract the folder to your desktop.
3. Get your file you need extracted and put it in the rarlabs folder.
4.Open up a console (also called a terminal) and type this:
```

cd Desktop/rarfolder
unrar e rarfile.rar

```
Change rar folder and rarfile.rar to your rar file and the folder's name.
Then it will extract everything in the current directory.
It is not -e also, just e.
Work?

---

### Post by Qwerty_ on 2006-10-04
Ok followed your instructions but when trying to extract the rar i got this 

mike@123456:~/Desktop/rarfolder$ unrar e rarfile.rar
bash: unrar: command not found
mike@123456:~/Desktop/rarfolder$


I renamed the files to rarfile.rar and the folder as rarfolder, inside rarfolder is all the things that i extracted from the rarlabs file.

---

### Post by Ben Sprinkle on 2006-10-05
Erm, did you look in the rar folder and is there a 'unrar' application in there?

---

### Post by Qwerty_ on 2006-10-05
Yeah there is the unrar app in the folder.

---

### Post by Ben Sprinkle on 2006-10-05
```

unrar e rarfile.rar

```
That's all you have to do. :)

---

### Post by Qwerty_ on 2006-10-05
Nah i downloaded it again and i get the same

 bash: unrar: command not found
i guess ill just have to unrar in it windows.

Thanks very much for your help though Goast Spirit i appreciate it.

---

### Post by Ben Sprinkle on 2006-10-05
It's not that hard to do, you must not be doing something right.
```

'unrar' e 'pathtorarfile.rar'

```
Try the 's.

---

### Post by Qwerty_ on 2006-10-05
Yeah i think the problem could my install but i doubt messing with wine would cause this ok when i am in the folder and i type in unrar i get the following:

```


mike@123456:~/Desktop/rarlinux-3.6.0(2).tar.gz_FILES/rar$ unrar
bash: unrar: command not found


```

That i think is where the problem lies.

---

### Post by Ben Sprinkle on 2006-10-05
You are running from the tar package? That's your problem then. Extract it.

---

### Post by Qwerty_ on 2006-10-05
No that is the name of the extracted file i am in another folder in that called rar.

---

### Post by jaboua on 2006-10-05
It doesn't look like he is in an archive but in a folder... However, remember that in order to run a command in current directory, you have to prefix it with "./" - in your situation, run "./unrar". IIRC the binary is named "rar" though (if you're speaking of the "real" rar).

---

### Post by Ben Sprinkle on 2006-10-05
./ Also means execute correct?
So if you did:
./txtfile.txt then the default text editor would open I think.

---

### Post by Qwerty_ on 2006-10-05
Yeah thanks ./unrar works cheers guys thanks alot.

---

### Post by Ben Sprinkle on 2006-10-05
Meh, finally this digital nightmare is over for you. :)

---

### Post by jaboua on 2006-10-05
> **Goat Spirit said:**
> ./ Also means execute correct?
So if you did:
./txtfile.txt then the default text editor would open I think.
Not really. When you normally run a command, it looks for the program in the directories mentioned in the variable named PATH ("echo $PATH"). For security reasons the current directory (".") is not in PATH by default (unlike DOS) - so you will have to provide the full path for the application/command. The dot means the path for the current location - so running ./unrar would be the same as giving the whole path /home/username/Desktop/unrar/unrar or something like that. When trying to run a textfile, it will likely give you a "permission denied" error as usually text-files are not given executable permissions - if it works however, the system will believe that the file is a script and try to execute it.

A few shortcuts worth knowing:
".."        Represents the parent folder
"."         Represents the current folder
"~"         Represents the home folder

---

### Post by Ben Sprinkle on 2006-10-05
I know some of that, example:
```

cd ../

```
But yes I know it can't execute text files now lol. It's for binary or shell scripts.

---

