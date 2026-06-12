---
title: "help executing a perl script"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by blahfod on 2008-02-16
Hi guys,

I have been an on again off again user since dapper, and I am now committed to losing windows all together. Something that will make this an easy transition is being able to use a particular perl script intended for batch renaming tvshows. it's called [http://robmeerman.co.uk/coding/file_renamer]("http://robmeerman.co.uk/coding/file_renamer")
the script is available in .pl format and when i download it and use it as instructed it returns errors at line 76, something to that extent. I have followed the recommendations in various posts such as changing the permissions and making it executable. what am i missing?

thanks for the help

blahfod

---

### Post by spiderbatdad on 2008-02-16
You didn't mention whether you are using 7.10 now. ```
perl -v
``` will list the version of perl you have installed. Perhaps it doesn't match the version the program is written in. In which case, getting the necessary version from the synaptic package manager may solve the problem...or perhaps perltidy, or any number of the perl packages included in synaptic.

---

### Post by blahfod on 2008-02-16
thanks for the response, much appreciated
I am using perl v5.8.8, here is a paste of the error the terminal gives me:

Can't locate Compress/Zlib.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at tvrenamer.pl line 76.
BEGIN failed--compilation aborted at tvrenamer.pl line 76.

---

### Post by spiderbatdad on 2008-02-16
```
sudo apt-get install libperl-dev
``` 
Might need the perl dev libraries for programs compiled with perlcc
???

---

### Post by blahfod on 2008-02-16
thanks again, but same error as above. I don't get it??? I am really new to this so bear with me. 
I have read some things about converting the file from dos to unix. I have tried that. I have changed the permissions to make it executable, i am not sure what the error above means, it appears to me that i am missing libraries maybe??? not too sure... thank you so much for the replies.

BlahFod

---

### Post by spiderbatdad on 2008-02-17
You may need to convert the file from DOS line-endings to Unix ones. Popular utilities for this are &#8220;fromdos&#8221; and &#8220;dos2unix&#8221;. (taken from RobMeerman.co.uk. creator of the script.)

[http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/text-filter-tools.html](http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/text-filter-tools.html)

Looks like it isn't the simplest solution, but doable.

---

### Post by spiderbatdad on 2008-02-17
looking here: [http://robmeerman.co.uk/coding/file_renamer#download](http://robmeerman.co.uk/coding/file_renamer#download)  is the perl script only which should run on any computer. There a two downloads. One is for windows. The other is for *nix systems.

---

### Post by blahfod on 2008-02-17
yeah, i have tried this already as well. Let me aks you, if you were trying to use this script how would you?

Basically, i have made the folders as the website suggests, i have placed my .avi files in there and have also placed tvrenamer.pl in there. Then from the terminal i navigate to that folder and enter 

perl tvrenamer.pl

is this the right way?

---

### Post by spiderbatdad on 2008-02-17
looks like you are doing fine. The error seems to be related to a missing module ie, Compress:Zlib...all the necessary modules are included on the man page, and it says they are available through CPAN.

---

### Post by amingv on 2008-02-17
You need the zlib module for perl; just issue this command:

```
sudo apt-get install libio-zlib-perl
```

---

### Post by spiderbatdad on 2008-02-17
It may be ```
sudo apt-get install libio-compress-zlib-perl
```

---

### Post by blahfod on 2008-02-17
you guys are the kings. thank you so profusely for all your help. 
It works now...

blahfod

---

### Post by meermanr on 2008-04-28
Mostly for the google-hits: The download page for [tvrenamer.pl ]("http://robmeerman.co.uk/coding/file_renamer")has a trouble-shooting section which lists the Perl CPAN packages you need installed, including a copy'n'paste command to install them:

[http://robmeerman.co.uk/coding/file_renamer#perl_requirements_na_for_windows_executable](http://robmeerman.co.uk/coding/file_renamer#perl_requirements_na_for_windows_executable)

(PS - I'm the script author, so please *do* let me know of problems! :) )

---

