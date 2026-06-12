---
title: "How do I run perl scripts?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2006-08-28
I found scripts to port all my itunes statistics over to amarok but I dont have a clue on how to actually run the scripts?

any help? :KS

---

### Post by MrHorus on 2006-08-28
> **jcrnan said:**
> I found scripts to port all my itunes statistics over to amarok but I dont have a clue on how to actually run the scripts?

any help? :KS

```
perl <scriptname>
```

---

### Post by bernied on 2006-08-28
If the following:
#!/bin/perl
or something like it, is the first thing in the file, and that is the path to your perl interpreter/compiler binary, then just executing it by typing its name will work. This is how I learnt to write perl scripts. But if the path to the script is not in your $PATH then you need to point to it's location as well, like:
./perlscript
for example, if it were in the working directory.
The script also needs the executable flag(s) set - use chmod.

---

### Post by jcrnan on 2006-08-28
uhm, Im a bit more new to this then you might realize :p I didnt understand much of what you said.. I tried typing perl <path to the file> in terminal but it said it couldnt find the file or directory.. wich is kinda weird since I double checked it and it was correct as far as I could gather.. I have the files on my desktop atm.

So please someone explain it toughorly and if you use any advanced words or commands please explain what they do.

---

### Post by charbo on 2006-08-28
If you have a script called *script* on your Desktop, then you would type in the terminal
perl /home/YOUR_LOGIN_NAME/Desktop/*script*

Is this what you have tried? If not, then that is what MrHorus is telling you to do.
Can you tell us what you exactly typed? That might help us figure out what you are doing...

What bernied is telling you is this.
Look at the first line of the actual script file.
You could type 
less /home/YOUR_LOGIN_NAME/Desktop/*script*
to do this.  
See if the first line is 
#!/bin/perl
Just type q to get out of less.
If it was #!/bin/perl was the first line of the file, you don't need to type 
perl /home/YOUR_LOGIN_NAME/Desktop/*script*
but you can just type 
/home/YOUR_LOGIN_NAME/Desktop/*script*
to run the script.
But before trying to run the script, you need to make sure that the script is executable.
To make file executable, you use *chmod* command.
For example 
chmod a+x /home/YOUR_LOGIN_NAME/Desktop/*script*
will make your *script* executable by everybody.

I hope this helps.

---

### Post by jcrnan on 2006-08-28
Okey, so I got it running.. almost.. Im just not entirely used to linux beeing case-sensetive yet.

However I got an eror:

nan@THE-HOLY-LAPTOP:~$ perl /home/nan/Desktop/convert_itunes.pl
Can't locate Date/Manip.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/nan/Desktop/convert_itunes.pl line 37.
BEGIN failed--compilation aborted at /home/nan/Desktop/convert_itunes.pl line 37.
nan@THE-HOLY-LAPTOP:~$ perl /home/nan/Desktop/convert_itunes.pl
Can't locate Date/Manip.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/nan/Desktop/convert_itunes.pl line 37.
BEGIN failed--compilation aborted at /home/nan/Desktop/convert_itunes.pl line 37.
nan@THE-HOLY-LAPTOP:~$

line 37 in the script: 

use Date::Manip;

anyone know what the problem is?

---

### Post by bernied on 2006-08-29
> Can't locate Date/Manip.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.7 /usr/local/share/perl/5.8.7 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /home/nan/Desktop/convert_itunes.pl line 37.
My interpretation of this is that you're missing something from your perl installation, at least missing something that this particular script needs. So the missing thing looks like a perl module called Date/Manip. A quick google found me this:
[http://search.cpan.org/dist/DateManip/](http://search.cpan.org/dist/DateManip/)
where you may be able to download this module. I can't help you with installing it though. I would guess that you should put it in one of those places in that list above, since that is where perl is looking for it. There are some instructions for installing it in the link called INSTALL on that page.

You have reached the limit of my knowledge on this - anything else would be a guess (some of this already is).

You might want to have a look in the ubuntu repositories (use whatever you use to install software - maybe apt-get?) before you get this module from this site. It's possible that you can get it through apt-get or aptitude (or whatever), which would be much cleaner than messing about with source code, if that's what this is. You may, for instance, find that you get an error when you type the 'make' command, because your machine is not set up for compiling source. If this is the case, then you need to install the build-essential package.

---

### Post by jcrnan on 2006-08-29
AUTOMATIC INSTALLATION

To install, just type
  perl Makefile.PL
  make
  make test
  make install




I found that in the install thing, but I dont understand where I am supposed to write that? I hate when people say just write that to do such and such and dont tell me where to write it -_-

---

### Post by bernied on 2006-08-30
These are terminal commands, this is generally the place that people are telling you to write stuff - try aysiu's excellent tutorial:
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)

But, like I said, this module may be available through the ubuntu repositories and apt-get (or aptitude). This package might help:
libtime-modules-perl
It is in the universe repository, which you will need to enable - look around in the aptitude menu for how to do this.

Installing this package will be much easier than trying to compile source code.

Start to google (or other search engine) to find out how to do things. 
So try to google 'ubuntu repository universe' to find out how to enable a huge amount of software.

Most of the help I've given in this thread I have found through google - it's just a matter of knowing which words to use.
Also, many of the more experienced people put links in their signatures that lead to basic tutorials. 

And if you are a windows convert, remember how long it took you to learn how to do all the things you take for granted in windows. Linux is arguably more powerful - so there is (arguably - but not here please) more to learn.

---

