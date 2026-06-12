---
title: "Installing file types in Ubuntu?"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by jeffinhedon on 2005-12-22
Greetings folks
another dilemna here?
I would like to install a program I have downloaded onto the desktop of my Ubuntu setup.
The file type however is a "sh" at the end of the file
ie xarpm_v1.1.sh
So how do I nstall the program from this ????
It might helpful to be able to use Synaptic package manager
but perhaps theres a better way
Your advice would be very much appreciated
Cheers;)

---

### Post by audax321 on 2005-12-22
Files with sh at the end are shell scripts. To run them you can open up a terminal (Applications > Accessories > Terminal), go to the directory the file is in (cd /home/username/Desktop), and type:

sh <name of file>

If the file will not execute,

chmod 755 <name of file>

and try again.

---

### Post by jeffinhedon on 2005-12-22
Well thanks for that
Sadly the proggy is still not installed properly.....dont know why??
There is a folder with all the files in it
like 
home/geoff/desktop/VInstall
but If I try to run the EXE file that I think should run it ..nothing happens
There is a ini file that suggests to me that there may be something or file missing
but I dont know wot????
This is the price we pay for relying on Windows install progs ....cant see wot the faults are cos I'm so green about linux generally
Oh well I will keep at it:confused:

---

### Post by bscbrit on 2005-12-22
You cannot run an .EXE program under linux - it will not work (as you have discovered).  The .ini file is probably no use to you either.  Your initial query was regarding .sh files.  These can run under linux - indeed that is exactly what they are for.  You first have to make the file executable which was described in the response to your first post.  An alternative method would be to open a terminal, change to the directory in which your .sh file is located, and type

chmod +x yourfile.sh

If it doesn't like that, try it again but prefix the entire line with 'sudo'.  Then to run it you can either point and click under Gnome, or in the same terminal window, type

./yourfile.sh

The initial ./ (which is a 'shorthand' for 'this directory'0 is important.  Without it , the script will simply not start.  This is a valuable security feature which helps to prevent potentially malicious scripts from being activated by someone who has gained access to your home/user area via the internet, or by using other scripts.

However, I repeat, you cannot run Windows installers under linux.

---

### Post by bscbrit on 2005-12-22
What is the function of the program you are trying to install.  Have you looked for a linux / Ubuntu equivalent?

---

### Post by jeffinhedon on 2005-12-23
[QUOTE=bscbrit]What is the function of the program you are trying to install.  Have you looked for a linux / Ubuntu equivalent?[/QUOTE]

Well Folks thanks for the comments so far
I heartily agree that my knowledge of Linux is woefully and frustratingly inadequate
I do realise that its a whole different way of thinking and I am trying to understand and learn

The prog I am having difficulty with is an Amateur Radio prog called "xarpm"
It is a packet radio terminal prog that enables one to log on to a BBS and download and read bulletins also to send replies and or personal notes to other radio hams..among other things
It supposed to be similar to a very good Windows type prog called Winpack which I have been usingr years
The prog that is proving difficult for me to deal with consists of a sh file
Now I have run this as suggested and it now says that there is an directory already in existance and that errors have occured
I suppose it may be a good idea to try and get rid of all existing "stuff" and start again
So how would I do that ...whats next??
As a Ubuntu newbie of only a couple of weeks I have only had experience of installing using the Synaptic Program manager so that it 
Sorry for the verbosity:smile:

---

### Post by rob2nd9th on 2005-12-23
I am going through the same prosses - But Iv been at it a few week longer, Iv backed up importat stuff and just played (reformated twice) then something cliks and bingo not an expert but conferdent user - the real trick is know when you are out of your depth and ask, "we have all been there" :smile:

---

### Post by bscbrit on 2005-12-23
OK, I used to be a SWL many years back but never became a Ham.

In my synaptic, if I choose sections in the bottom left of the window, one of the displayed sections is Amateur Radio.  Although I understand what you have written, I do not know if any of the over 100 programs might be the equivalent to the one you are looking for, but 'xastr' looks promising.  Is this any use to you?

EDIT: If not, then we will press on trying to install the package that you have.....

---

### Post by jeffinhedon on 2005-12-24
[QUOTE=bscbrit]OK, I used to be a SWL many years back but never became a Ham.

In my synaptic, if I choose sections in the bottom left of the window, one of the displayed sections is Amateur Radio.  Although I understand what you have written, I do not know if any of the over 100 programs might be the equivalent to the one you are looking for, but 'xastr' looks promising.  Is this any use to you?

EDIT: If not, then we will press on trying to install the package that you have.....[/QUOTE]

 think the problem looks like ..I appear to have some shared library files missing 
When I tried to run the prog
I got an error ........something like 
libsldc++ -libc6.1.s..z
Something like that anyway
I would have to copy the message exactly if it was thought to be the relevant problem area
Any ideas folks
still :confused:

---

### Post by bscbrit on 2005-12-24
Yes - load the missing file.:p 

Try searching in synaptic for the file that is missing e.g. libc6 or whatever.  Its in my repos and should be easy to install.

Then try your build or installation again.

---

