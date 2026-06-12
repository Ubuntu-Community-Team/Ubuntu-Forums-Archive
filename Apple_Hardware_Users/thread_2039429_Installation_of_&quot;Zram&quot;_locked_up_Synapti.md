---
title: "Installation of &quot;Zram&quot; locked up Synaptic"
date: 2012-08-08
forum: Apple Hardware Users
---

### Post by Javelin Dan on 2012-08-08
Running Ubuntu 12.04 on an eMac G-4, 1 Ghz processor, 1 GB Ram, 40 GB hard drive. 

I had looked on a site entitled "Modify Ubuntu - Ubuntu 12.04 Tips and Tricks" and decided I would try installing "Zram" to maybe speed things up. It seemed to install normally through the command line, but when I went into Synaptic for something else it told me to run "dpkg". I did, and ran the command:

[*sudo dpkg --debug=<octal>*] and got the following output:

[                           *[SIZE=2]dpkg: error: unknown option -o [/SIZE]* 
  
 [I][SIZE=2]Type dpkg --help for help about installing and deinstalling packages 
[*]; [/SIZE][/I] 
 *[SIZE=2]Use `dselect' or `aptitude' for user-friendly package management; [/SIZE]* 
 *[SIZE=2]Type dpkg -Dhelp for a list of dpkg debug flag values; [/SIZE]* 
 *[SIZE=2]Type dpkg --force-help for a list of forcing options; [/SIZE]* 
 *[SIZE=2]Type dpkg-deb --help for help about manipulating *.deb files; [/SIZE]* 
  
 [I][SIZE=2]Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ! [/SIZE][/I] 
 *[SIZE=2]daniel@daniel-desktop:~$ sudo dpkg -Dhelp [/SIZE]* 
 *[SIZE=2]dpkg debugging option, --debug=<octal> or -D<octal>: [/SIZE]* 
  
  *[SIZE=2]Number  Ref. in source   Description [/SIZE]* 
       *[SIZE=2]1  general          Generally helpful progress information [/SIZE]* 
       *[SIZE=2]2  scripts          Invocation and status of maintainer scripts [/SIZE]* 
      *[SIZE=2]10  eachfile         Output for each file processed [/SIZE]* 
     *[SIZE=2]100  eachfiledetail   Lots of output for each file processed [/SIZE]* 
      *[SIZE=2]20  conff            Output for each configuration file [/SIZE]* 
     *[SIZE=2]200  conffdetail      Lots of output for each configuration file [/SIZE]* 
      *[SIZE=2]40  depcon           Dependencies and conflicts [/SIZE]* 
     *[SIZE=2]400  depcondetail     Lots of dependencies/conflicts output [/SIZE]* 
   *[SIZE=2]10000  triggers         Trigger activation and processing [/SIZE]* 
   *[SIZE=2]20000  triggersdetail   Lots of output regarding triggers [/SIZE]* 
   *[SIZE=2]40000  triggersstupid   Silly amounts of output regarding triggers [/SIZE]* 
    *[SIZE=2]1000  veryverbose      Lots of drivel about eg the dpkg/info directory [/SIZE]* 
    *[SIZE=2]2000  stupidlyverbose  Insane amounts of drivel [/SIZE]* 
  
 *[SIZE=2]Debugging options can be mixed using bitwise-or. [/SIZE]* 
 *[SIZE=2]Note that the meanings and values are subject to change. [/SIZE]* 
 *[SIZE=2]daniel@daniel-desktop:~$ sudo dpkg --debug=<octal> [/SIZE]* 
 *[SIZE=2]bash: syntax error near unexpected token `newline' [/SIZE]* 
 *[SIZE=2]daniel@daniel-desktop:~$ sudo dpkg --D<octal> [/SIZE]* 
 *[SIZE=2]bash: syntax error near unexpected token `newline' [/SIZE]* 
 [SIZE=2]*daniel@daniel-desktop:~$]*[/SIZE]


[SIZE=2]I'm lost at this point and could use some help.[/SIZE]

---

### Post by Javelin Dan on 2012-08-09
I removed "Zram" and got synaptic back. I still don't know why it didn't work, but I guess this is as "Solved" as it's gonna get.

---

