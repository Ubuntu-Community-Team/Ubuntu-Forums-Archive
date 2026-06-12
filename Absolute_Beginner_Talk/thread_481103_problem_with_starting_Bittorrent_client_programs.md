---
title: "problem with starting Bittorrent client programs"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by h2OPiR on 2007-06-22
hello community 8-) (this is my first post)

 i run  ubuntu 7.04 (feisty)

 when i click for open   Deluge or Azureus  this programs try to open  ,not open

...how can i fix this?

---

### Post by walkerk on 2007-06-22
try opening through a terminal and post any errors so we know whats going on..

in terminal:
Azureus
```
azureus
```

Deluge
```
deluge
```
```
deluge-torrent
```

---

### Post by clawoo on 2007-06-22
Hi, experiencing the same thing. When running deluge from a terminal it outputs the following:

```
$ deluge
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)
```

I tried removing & reinstalling the bittorrent and deluge-torrent packages but to no avail. :(

---

### Post by supersonicdarky on 2007-06-22
i prefer ktorrent. try it.

---

### Post by h2OPiR on 2007-06-22
i hope this help...

         ->for azureus

... " An unexpected exception has been detected in native code outside the VM.
Unexpected Signal : 11 occurred at PC=0xA974D172
Function=(null) " ....

... " Heap at VM Abort:
Heap
 def new generation   total 576K, used 493K [0xab980000, 0xaba20000, 0xabe60000)
  eden space 512K,  89% used [0xab980000, 0xab9f27f8, 0xaba00000)
  from space 64K,  54% used [0xaba10000, 0xaba18cc8, 0xaba20000)
  to   space 64K,   0% used [0xaba00000, 0xaba00000, 0xaba10000)
 tenured generation   total 4436K, used 2660K [0xabe60000, 0xac2b5000, 0xaf980000)
   the space 4436K,  59% used [0xabe60000, 0xac0f92f8, 0xac0f9400, 0xac2b5000)
 compacting perm gen  total 12032K, used 11895K [0xaf980000, 0xb0540000, 0xb3980000)
   the space 12032K,  98% used [0xaf980000, 0xb051df50, 0xb051e000, 0xb0540000)

Local Time = Fri Jun 22 22:32:30 2007
Elapsed Time = 7
#
# The exception above was detected in native code outside the VM
#
# Java VM: Java HotSpot(TM) Client VM (Blackdown-1.4.2-02 mixed mode)
#
# An error report file has been saved as hs_err_pid15825.log.
# Please refer to the file for further information.
#
Aborted (core dumped) " 


         ->for deluge

no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Torrent Size 12621765.0
Available Space 45941039104
Torrent Size 2218087.0
Available Space 45941039104
Torrent Size 7057172.0
Available Space 45941039104
Torrent Size 1057935.0
Available Space 45941039104
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)



:confused:   :roll:

---

### Post by theonlyalterego on 2007-06-22
You may want to check out this deluge bug: [#215]("http://dev.deluge-torrent.org/ticket/215") it doesn't seem to list a solution that I can see, however it's listed as close...:confused:

---

### Post by Nussbaum on 2007-06-22
I have with Azureus when I exit the program sudden that it refuses to start again. Basically it starts and immediatly closes again. I fix this by going to the '/home/<yourhomedir>/.azureus/logs' directory and delete all files. Then I go to the 'save' sub-directory and delete all files there. I don't know if it helps for you but it might be worth a try.

---

### Post by NeoLithium on 2007-06-22
For deluge, you're best off removing that package, and then going to [http://www.getdeb.net](http://www.getdeb.net)  There is a version of deluge there that I know works, as I installed that one myself.  Perhaps it might be the best alternative.

---

### Post by amazingtaters on 2007-06-22
try Ktorrent. It is made of win and work.

---

### Post by h2OPiR on 2007-06-23
I have completed removed   Bit torrent & Deluge(0.5.1.1) , and then installed again 
....unfortunately the same problem  :!:

....i  used Ktorrent , but i thing (don't know much) is better to run for gnome gui , gnome programs

---

### Post by h2OPiR on 2007-06-23
any  idea guys  :?:

---

### Post by ArchVile on 2007-06-24
i had the same problem (deluge 0.5.0 on feisty32), without discernable cause after a reboot. maybe some lib update affecting deluge 0.5.0.

try the following:
1. cave your .torrent files and partially downloaded files.
2. "completely remove" deluge with synaptic.
3. go to ~/.config and do > rm -r deluge
4. go to getdeb.org and install deluge 0.5.1.1 from there

worked for me. you will probably have to restore your downloads. i don't know the official procedure, but i always...

1. start the new deluge version and set my options
2. re-add the old .torrent files to deluge as if they were new
3. let deluge start downloading (and let it create new data files)
4. close deluge (completely!),
5. and then replace the newly created data files with my old ones.
6. restart deluge, let it check the files, et voila!

---

### Post by atria on 2007-06-24
Weird, Azureus works perfectly fine here and i just retried it. I'm using java6-jre-bin if that helps. Uninstall any java runtimes that you currently have and do this:

```
sudo aptitude install java6-jre-bin
```

and try executing azureus with ./azureus

I downloaded azureus from azureus.sf.net as opposed to the one in the ubuntu repositories. Have fun.

---

### Post by h2OPiR on 2007-06-25
problem fixed ! 
 thank you all for you help  (y)  :cool:

---

