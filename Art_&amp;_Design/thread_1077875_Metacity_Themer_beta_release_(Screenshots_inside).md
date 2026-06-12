---
title: "Metacity Themer beta release (Screenshots inside)"
date: 2009-02-22
forum: Art &amp; Design
---

### Post by days_of_ruin on 2009-02-22
EDIT: Metacity Themer 0.2 release, read more here.[https://launchpad.net/mct/+announcements]("https://launchpad.net/mct/+announcements")

---

### Post by UbuntuNerd on 2009-02-22
Im about to try this there are a few things i like to change in my current theme.:)

---

### Post by MetalMusicAddict on 2009-02-22
Great! You have a message on the Ubuntu-Art mailing list. Please don't post the full-size images here though. Thumbnails that link to full-size would be better.

---

### Post by days_of_ruin on 2009-02-22
> **MetalMusicAddict said:**
> Great! You have a message on the Ubuntu-Art mailing list. Please don't post the full-size images here though. Thumbnails that link to full-size would be better.

Sorry, I guess the first one could've been smaller.But I wanted the screenshots in the post itself so its easier to read.(Not "see attachment 2" etc)

---

### Post by Neon Lights on 2009-02-22
do haz problemz. XD

I hit open, it opens to my ~./themes...but then, I can't open anything there in the program. (open button is grayed out no matter what I select).

wat I'z doin wrong? D:

---

### Post by days_of_ruin on 2009-02-22
> **Neon Lights said:**
> do haz problemz. XD

I hit open, it opens to my ~./themes...but then, I can't open anything there in the program. (open button is grayed out no matter what I select).

wat I'z doin wrong? D:

Are you sure you have metacity themes installed there?NOT gtk themes.They have to be folders to not archives.

---

### Post by UbuntuNerd on 2009-02-22
same here no matter what I do I can't select anything?

---

### Post by days_of_ruin on 2009-02-22
I guess I didn't make this clear enough.
You select ~/.themes/themeyouwantotedit folder.
Don't double click on any folder.You should see a preview of the theme on the
right side of the dialog.See the first screenshot again.

---

### Post by UbuntuNerd on 2009-02-22
Ok I got it now is working good I like it good job man :) I will explore this further I'll let you know how it goes.

---

### Post by days_of_ruin on 2009-02-22
> **UbuntuNerd said:**
> Ok I got it now is working good I like it good job man :) I will explore this further I'll let you know how it goes.

Okay:D

---

### Post by Neon Lights on 2009-02-22
Gahhh, still can't get it to work, feeling like an idiot here >.< I hit open, I select the folder of one of the themes (not an archive, has a metacity-1 folder in it). I don't see the preview though. Even downloaded the Vrey theme just to see if it was a problem with the themes. :/ no go.

---

### Post by days_of_ruin on 2009-02-22
> **Neon Lights said:**
> Gahhh, still can't get it to work, feeling like an idiot here >.< I hit open, I select the folder of one of the themes (not an archive, has a metacity-1 folder in it). I don't see the preview though. Even downloaded the Vrey theme just to see if it was a problem with the themes. :/ no go.

Mind posting a screenshot?Also try running it from the command line to see
if there is any output.

---

### Post by Neon Lights on 2009-02-22
Sure, here ya go.
I'm on Jaunty, I wonder if that would be affecting anything?
No terminal output.

---

### Post by days_of_ruin on 2009-02-22
> **Neon Lights said:**
> Sure, here ya go.
I'm on Jaunty, I wonder if that would be affecting anything?
No terminal output.

Try this:```
cd pathtometacitythemerfolder
cd src
python theme_test.py Vrey
```

That should print "Valid".

---

### Post by Neon Lights on 2009-02-22
> **days_of_ruin said:**
> Try this:```
cd pathtometacitythemerfolder
cd src
python theme_test.py Vrey
```That should print "Valid".
Yep. Says "Valid".

---

### Post by days_of_ruin on 2009-02-22
> **Neon Lights said:**
> Yep. Says "Valid".

So the open button is grayed out?And none of the themes open?

---

### Post by days_of_ruin on 2009-02-22
Replace src/main.py with the attached file and try again and post the output.

---

### Post by Neon Lights on 2009-02-23
> **days_of_ruin said:**
> Replace src/main.py with the attached file and try again and post the output.
No difference, no output (other than murrine complaining about the theme using deprecated things)
And yeah, none of the themes open, grayed out Open button.

---

### Post by days_of_ruin on 2009-02-23
Oops I forgot to change the right thing, try again.

---

### Post by Neon Lights on 2009-02-23
Yay! That works perfectly. :] Thanks!

---

### Post by Orlsend on 2009-02-23
I will be trying this out, would be cool if you enabled the translations at launchpad.

---

### Post by days_of_ruin on 2009-02-23
> **Orlsend said:**
> I will be trying this out, would be cool if you enabled the translations at launchpad.

Do you know of any good tutorials for using translations in pygtk?

---

### Post by days_of_ruin on 2009-02-23
> **Neon Lights said:**
> Yay! That works perfectly. :] Thanks!

It really should have worked without the changes I made.Must be something
in jaunty.

Btw please post the new output.

---

### Post by Neon Lights on 2009-02-24
> **days_of_ruin said:**
> It really should have worked without the changes I made.Must be something
in jaunty.

Btw please post the new output.
Guess soo.

No output for most themes, however when opening the Doka theme, it gives out ```
Valid
Traceback (most recent call last):
  File "/home/person/Desktop/0.1-beta/src/main.py", line 909, in on_toolbar_open_clicked
    self.open()
  File "/home/person/Desktop/0.1-beta/src/main.py", line 944, in open
    self.load_theme(self.theme_file)
  File "/home/person/Desktop/0.1-beta/src/main.py", line 986, in load_theme
    self.TE = TE2.Theme(theme_file,restore)
  File "/home/person/Desktop/0.1-beta/src/TE2.py", line 92, in __init__
    self.load()
  File "/home/person/Desktop/0.1-beta/src/TE2.py", line 283, in load
    self.make_drawops('~FOO_do~',True)
  File "/home/person/Desktop/0.1-beta/src/TE2.py", line 513, in make_drawops
    tag = self.root[i].tag
  File "/usr/lib/python2.5/xml/etree/ElementTree.py", line 224, in __getitem__
    return self._children[index]
IndexError: list index out of range

```and doesn't open it.


Also noticed, it doesn't show the preview of the theme in the file browser. It opens a side pane like it should, but it's empty.

---

### Post by days_of_ruin on 2009-02-25
> **days_of_ruin said:**
> Do you know of any good tutorials for using translations in pygtk?

Never mind I found one.I am now working on making this translatable.:guitar:


I am also working on make a deb for this, what category should this go in?
I am thinking accessories or graphics.

---

### Post by Interpreter on 2009-02-25
Subscribed to this, kraut translator waiting.....

---

### Post by Orlsend on 2009-02-25
> **days_of_ruin said:**
> Never mind I found one.I am now working on making this translatable.:guitar:


I am also working on make a deb for this, what category should this go in?
I am thinking accessories or graphics.

Well I know for sure you will have a full Spanish translation.

---

### Post by ricsi-pontaz on 2009-02-26
Hi!

I think this program is a good idea! 
I can translate it to hungarian if you want. :)

---

### Post by days_of_ruin on 2009-02-26
> **ricsi-pontaz said:**
> Hi!

I think this program is a good idea! 
I can translate it to hungarian if you want. :)

Thanks.I will be releasing a deb and uploading the translation template
soon stay tuned.

---

### Post by days_of_ruin on 2009-02-28
I uploaded the translation template but it has to wait for [review]("https://translations.launchpad.net/mct/trunk/+imports").
You can download it anyway you just can't translate it inside launchpad yet.

When some of the translations are ready I will make the next release 0.1.3.
It adds some new features including copying and pasting drawops child elements.

---

### Post by Interpreter on 2009-03-01
No worries with the review part..."normal".

---

### Post by days_of_ruin on 2009-03-02
The translation template is now uploaded!
[https://translations.launchpad.net/mct/trunk]("https://translations.launchpad.net/mct/trunk")

---

### Post by Orlsend on 2009-03-03
Cool now its time to work!

---

### Post by ricsi-pontaz on 2009-03-03
I finished the translation. ;)

---

### Post by Orlsend on 2009-03-04
I did too for spanish. When will the .deb be released?

---

### Post by Flimm on 2009-03-04
This is one awesome project. I can't tell you how excited I was to see dynamic preview generation for Metacity themes. This is something which I was hoping to include in [Epidermis](https://launchpad.net/epidermis), but as I didn't know C, I couldn't examine the code in the appearance app. Now I can examine your code (thanks for making it free, by the way) and see if I can make Epidermis better. If you want other developers on your project, give me a shout, I'll send stuff in once exams are over. For example, I could help you make a deb.

---

### Post by ricsi-pontaz on 2009-03-05
We wait for the Metacity Themer 0.1.3 :) :popcorn:

---

### Post by Flimm on 2009-03-05
I packaged Metacity Themer into a .deb, you can get it from [my PPA](https://launchpad.net/~flimm/+archive/ppa/) and you can get the code from [my bazaar branch](https://code.launchpad.net/~flimm/mct/packaging) at Launchpad. It's the latest version from upstream, I labeled it as 0.1beta1 , but I don't know if that's correct.
EDIT: I've corrected it to 0.9~alpha1 , it's now ready to be merged!

---

### Post by days_of_ruin on 2009-03-05
> **Flimm said:**
> I packaged Metacity Themer into a .deb, you can get it from [my PPA](https://launchpad.net/~flimm/+archive/ppa/) and you can get the code from [my bazaar branch](https://code.launchpad.net/~flimm/mct/packaging) at Launchpad. It's the latest version from upstream, I labeled it as 0.1beta1 , but I don't know if that's correct.

I wouldn't do that.My last commit had a lot of bugs.Wait till I upload my latest commit.

---

### Post by Flimm on 2009-03-05
> **days_of_ruin said:**
> I wouldn't do that.My last commit had a lot of bugs.Wait till I upload my latest commit.
OK, I've subscribed to the branch, so I'll know when you're ready.

---

### Post by days_of_ruin on 2009-03-05
> **Flimm said:**
> OK, I've subscribed to the branch, so I'll know when you're ready.

Don't make a deb as soon as its released.I want people to just get a copy of the branch and test it for bugs.

---

### Post by days_of_ruin on 2009-03-05
I have uploaded a new pot file so there are now a few more strings to translate.

Btw the latest commit I posted message is wrong.Translations are working.

---

### Post by ricsi-pontaz on 2009-03-08
Any news about the project?

---

### Post by days_of_ruin on 2009-03-08
> **ricsi-pontaz said:**
> Any news about the project?

* I am done working on the icons.:D (Check out by going to the launchpad page
* metacity-themer can now open themes from the command line.
* You can copy and paste draw ops child elements (image,line,rectangle etc..) from one window to another.

* Improved the about dialog.

I will *probably* be releasing a .deb this week.
But I am not going to include translations that aren't complete so translators please help finish them.

---

### Post by ricsi-pontaz on 2009-03-09
> **days_of_ruin said:**
> * I am done working on the icons.:D (Check out by going to the launchpad page
* metacity-themer can now open themes from the command line.
* You can copy and paste draw ops child elements (image,line,rectangle etc..) from one window to another.

* Improved the about dialog.

I will *probably* be releasing a .deb this week.
But I am not going to include translations that aren't complete so translators please help finish them.

Good job! Thanks \\:D/

---

### Post by days_of_ruin on 2009-03-17
Metacity Themer 0.2 Released!
Get it from source or the ppa
[https://launchpad.net/mct/+announcement/2241]("https://launchpad.net/mct/+announcement/2241")

---

### Post by ricsi-pontaz on 2009-03-17
Cool! :)

I wrote a blog post about it on the hungarian ubuntu Loco's website

---

### Post by days_of_ruin on 2009-03-17
> **ricsi-pontaz said:**
> Cool! :)

I wrote a blog post about it on the hungarian ubuntu Loco's website

Nice! It looks like a good post altho I can't understand it.
You should do one in english.:P

---

### Post by ricsi-pontaz on 2009-03-18
I've got a problem. Somebody installed Metacity Themer 0.2b, but when he want to start it, he got an error message:

> Traceback (most recent call last):
File "/usr/bin/metacity-themer", line 4, in
import dl
ImportError: No module named dl

Do you know the solution?

---

### Post by days_of_ruin on 2009-03-18
> **ricsi-pontaz said:**
> I've got a problem. Somebody installed Metacity Themer 0.2b, but when he want to start it, he got an error message:



Do you know the solution?

dl is part of the python standard library.I don't know why he doesn't have it.What ubuntu version and python version is he using?

---

### Post by ricsi-pontaz on 2009-03-20
> **days_of_ruin said:**
> dl is part of the python standard library.I don't know why he doesn't have it.What ubuntu version and python version is he using?

The Ubuntu verison is 8.10 and the python is the default in the system, so 2.5.2-11.1ubuntu1

---

### Post by TheDexter1111 on 2011-03-23
sorry to bring up an old topic... should probably start a new one, but ill try here first..

I've downloaded the 'metacity-themer_0.2-0ubuntu0~ppa1_all.deb' but when i double click on it I get this

Error: Dependency is not satisfiable: python2.5 (>= 2.5.2)

am i just a complete noob or is their a way to remedy this...? 

im on Lucid 10.04
cheers for any help :)

---

### Post by 23dornot23d on 2011-03-23
What version of python do you have installed  ?

sudo apt-get install python

may sort you out if you do not have it installed ......

---

### Post by TheDexter1111 on 2011-03-23
dave@laptop:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

so it looks like its 2.6.5 not 2.5.2... surely the newer version would suffice?

---

### Post by 23dornot23d on 2011-03-23
> 
Error: Dependency is not satisfiable: python2.5 (>= 2.5.2)

I agree .... the error states python needs to be greater or equal to 2.5.2 
and you have 2.6.5 so it should be ok .......


Have you tried installing it [from the PPA ....]("https://launchpad.net/%7Efreshapplepy/+archive/ppa")

may give you a better error report from here ,,, looking back through this old thread there
was a problem with python ..... ( and I cannot see that it was resolved on here )

---

### Post by TheDexter1111 on 2011-03-23
hmmm how? i have followed the instructions on Isaiah's page.. I added the 2 lines to the sources list.. as strangly:

dave@laptop:~$ sudo apt-get-repository ppa:freshapplepy/ppa
sudo: apt-get-repository: command not found

so I added the lines manually, did the 'key' thing


dave@laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 90300295
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 90300295
gpg: requesting key 90300295 from hkp server keyserver.ubuntu.com
gpg: key 90300295: "Launchpad PPA for Isaiah Heyer" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


now what? where/how do i install it>? there is no link on his page to download.

sorry, im not to savy with installing packages yet :P but thank you for your help so far :)

---

### Post by TheDexter1111 on 2011-03-23
sorry, double posted

---

### Post by 23dornot23d on 2011-03-23
There appears to be a problem with that package ...... I have just tried it myself and even installed python 2.5.2

and it still throws up that error .......... sorry ....  

( Installing the PPA it should have appeared in Synaptic Package Manager after a update and it did not appear to be there )


           [IMG]http://img39.imageshack.us/img39/1710/pyerror.jpg[/IMG]


The original author of this package needs to look at it .........

Its nothing you have done wrong ..... the package appears to be broken.

---

### Post by TheDexter1111 on 2011-03-23
ok no worries then.. I thought it would appear in synaptic too but no dice.. anyway, thank you for your help, its much appreciated :D

---

### Post by moongia on 2011-03-31
iam i missing some thing iam getting this err,with ubuntu 10.10 32bit


nik@LINUX:~$ metacity-themer
Traceback (most recent call last):
  File "/usr/local/bin/metacity-themer", line 17, in <module>
    from metacity_themer import main, utils
  File "/usr/local/lib/python2.6/dist-packages/metacity_themer/__init__.py", line 115, in <module>
    from metacity_themer.main import main
  File "/usr/local/lib/python2.6/dist-packages/metacity_themer/main.py", line 30, in <module>
    import metacity
ImportError: No module named metacity
nik@LINUX:~$

---

### Post by Flimm on 2011-03-31
Try installing python-metacity:
```
sudo apt-get install python-metacity
```

---

### Post by 23dornot23d on 2011-03-31
I have just done that too ..... 

sudo apt-get install python-metacity

even after installing the python-metacity I am getting the error I had previously ..... 

Error: Dependency is not satisfiable: python2.5 (>= 2.5.2)

but it does not say anything about the wrong architechture .... is it ok on Ubuntu 10.10 ... 64 bit ...
on the install screen ...... was just when I re-read the ppa ...... that I noticed it ...........
is there a way it  can work for 64 bit ....... too ...... ?

Downloaded it from here now and ran the [python setup]("https://launchpad.net/mct/+download") too but no luck yet .....

but there is a build folder now for 64 bit ... still no luck in running it ....

Got it - now ..... may have been due to not having GLADE installed .......

To run it the command I used is below .... after downloading and using the python scripts in it .....

keith@keith-Aspire-7730ZG:~/Downloads/metacity-themer-0.2.1/build/scripts-2.6$ python metacity-themer

[IMG]http://img28.imageshack.us/img28/1517/deb1.jpg[/IMG]


There is another build too 0-2.2 ...... will see if I can find the python source for it .....

Will still not install from ppa ..... in Software Centre .... as that version is 0.2.2 

Still comes up with this error 

Error: Dependency is not satisfiable: python2.5 (>= 2.5.2)

Yet I am running the version 0.2.1 .... now on Ubuntu 10.10 .... 64 bit .....

Question [about what files it opens]("https://answers.launchpad.net/mct/+question/98563")

Not managed to open a Theme yet with it ......

---

