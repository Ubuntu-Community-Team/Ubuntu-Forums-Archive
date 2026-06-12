---
title: "Clit Error Question"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by da5id on 2006-04-12
I DL'd a pkg I need to read *my* MS Reader ebooks in my shiny *new* OS, Ubuntu, from [http://www.kyz.uklinux.net/convlit.php](http://www.kyz.uklinux.net/convlit.php)

The directions say: 

To compile and install the program goes *something* like this [emphasis added]:

$ gzip -cd < open_c-lit.tar.gz | tar xf -
$ cd cl?t14src/lib
$ make
$ cd ../cl?t14
$ make
# install cl?t /usr/local/bin

A copy of my term results, all errors, is attached as a text file.  Any suggestions will be appreciated.

--Gene

PS I tried to copy term text to Open Office Writer so colors would be visible, but "paste" into Writer did nothing -- just a blank page.  Is a copy and paste from Terminal special -- eg, you can only paste to a plain txt program?

NB  I am an ABSOLUTE BEGINNER still working on my bash tutorials.  So "Just ./configure, make, makeinstall the regular way," responses will be less than helpful.;)    


 

The final command is executed as root. The question marks are wildcards, purely for keeping this web-page available to everybody. You can put the letter i in their place, should it amuse you.

---

### Post by therunnyman on 2006-04-12
I so want to help with this, but I can't.  I'm sorry.

The reason I'm responding is because you may want to contact someone about the name of this package.  Far be it from me to interfere with free speech, but, uh, I don't know if children shouldn't be exposed to that kind of language when first encountering The Brothers Karamazov.  Anais Nin, maybe, but certainly not Dostoyevsky.

Wheaties, The breakfast of champions.

therunnyman

---

### Post by Digitallysick on 2006-04-12
When you get Clit errors, that probably means your not taking her out to dinner, or listening to her true feelings. And if you dont put up with that bs, the Clit will just disappear! sudo apt-get laid

---

### Post by mrchrisblau on 2006-04-13
[QUOTE=Digitallysick]When you get Clit errors, that probably means your not taking her out to dinner, or listening to her true feelings. And if you dont put up with that bs, the Clit will just disappear! sudo apt-get laid[/QUOTE]

I feel so dirty laughing at that.. but geeky at the same time ("sudo apt-get laid".. lolers!). :D

---

### Post by futz on 2006-04-22
[QUOTE=da5id]The directions say: 
$ gzip -cd < open_c-lit.tar.gz | tar xf -
$ cd cl?t14src/lib
$ make
$ cd ../cl?t14
$ make
# install cl?t /usr/local/bin
[/QUOTE]
These directions are totally bogus. Look in the README file for slightly more correct instructions. I'll attempt to make them clearer and more correct in the following text:

Before you start, you'll likely need the build-essential package. Install it with Synaptic and then continue.

First, unpack the compressed file into a directory. You've likely already done that.

Then, in a terminal, cd (change directory) to the "the_clit" directory. Now cd again to "lib". Type "make" (without the quotes). A bunch of text will speed by, with several warnings. Ignore them. It should be fine unless it fails with errors.

Next, type "cd .." (without quotes - leave em out on all my instructions). "cd .." means change directory up one level. Then type "cd clit12".

Type "make" again. Again a bunch of text will fly by as the program gets compiled. There will be several warnings. Ignore them. All will be fine unless errors occur.

That's it. You've built c-lit. To start the program you'll have to be in the clit12 directory - type "./clit12" without any parameters for instructions.

---

### Post by futz on 2006-04-22
Ok, the instructions given when you type "./clit12" are wrong too. I'll attempt to clarify here. Say I want to convert a file in my download directory called "bear.lit" and dump the result into the clit12 directory: 

cd to the clit12 directory and type this:
```
 ./clit12 /home/futz/download/bear.lit .
```
That last period means use the current directory as the destination. I could just as easily dump the result into my download directory instead, with:
```
 ./clit12 /home/futz/download/bear.lit /home/futz/download
```

Unfortunately, clit12 doesn't recognize my lit file as a lit file. It says:
```
Error reading file "/home/futz/download/bear.lit" --
        This file does not appear to be a .LIT file.

```

Sigh...

---

### Post by futz on 2006-04-22
Tried a different lit file and it works fine. That first one was incompatible in some way. The program breaks the book out into multiple .htm files, so you can view it with a web browser.

Oh ya, you will find that typing book filenames with spaces into the terminal won't work. For instance, if you do it like this:
```
$ ./clit12 /home/futz/download/Anthony, Piers - Xanth 25 - Swell Foop.lit /home/futz/download
```
it won't work. To get around this, either rename your file to a simple one word filename for simple typing, or wrap (delimit) the file path in quotes like this:
```
$ ./clit12 "/home/futz/download/Anthony, Piers - Xanth 25 - Swell Foop.lit" /home/futz/download
```
Good luck...

---

### Post by OffHand on 2006-04-22
[QUOTE=Digitallysick]When you get Clit errors, that probably means your not taking her out to dinner, or listening to her true feelings. And if you dont put up with that bs, the Clit will just disappear! sudo apt-get laid[/QUOTE]
LOL  :mrgreen:

---

### Post by xenmax on 2006-04-22
perhaps, a mod or an admin might want to put a hyphen between C and l as is seen in name of the tar.gz?! :)

---

### Post by robenroute on 2006-05-11
Install the following (in this order), using "sudo dpkg -i <file name>":

1. [libtommath_0.37-1_i386.deb]("http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb")

2. [clit_1.8-1_i386.deb]("http://ace-host.stuart.id.au/russell/files/debian/sarge/clit/clit_1.8-1_i386.deb")

Now you can use the "clit" command to convert your .lit files. Use "clit ?" for more help. Good luck!

Rob


P.S. I installed it on Dapper and it works like a charm....

---

### Post by imageburn on 2006-11-05
Huh. trying to re-install after putting 6.10 up; the above method doesn't work. No archive of *either* exists. Love clit. Try to install manually.

---

### Post by ipreferpi on 2007-07-11
> **robenroute said:**
> Install the following (in this order), using "sudo dpkg -i <file name>":

1. [libtommath_0.37-1_i386.deb]("http://ace-host.stuart.id.au/russell/files/debian/sarge/libtommath/libtommath_0.37-1_i386.deb")

2. [clit_1.8-1_i386.deb]("http://ace-host.stuart.id.au/russell/files/debian/sarge/clit/clit_1.8-1_i386.deb")

Now you can use the "clit" command to convert your .lit files. Use "clit ?" for more help. Good luck!

Rob


P.S. I installed it on Dapper and it works like a charm....

Worked perfectly. Thank you

---

