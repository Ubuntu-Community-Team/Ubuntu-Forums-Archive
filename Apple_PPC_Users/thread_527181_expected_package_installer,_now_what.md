---
title: "expected package installer, now what?"
date: 2007-08-16
forum: Apple PPC Users
---

### Post by Jim Baker on 2007-08-16
I have a burned Feisty CD which I would like to install on my G3 Pismo (400/512). I found the command line "stuff". How do I use this to get started on my Mac?
Thanks,
JB

---

### Post by matthew.lns1 on 2007-08-16
I don't fully understand your query however all give it a shot. You having trouble installing ubuntu? Or a package? Your trying to run a script? IF your trying to install ubuntu you should just need to click install. You should just need to double click on an packeage to get installed. I don't know how to run a BASH script.

---

### Post by Jim Baker on 2007-08-19
The CD I burned from Feisty iso doesn't have any kind of clickable installer that I could find. Where is it supposed to be? If it's not there, then what?
Thanks,

---

### Post by Jim Baker on 2007-08-20
> **Jim Baker said:**
> The CD I burned from Feisty iso doesn't have any kind of clickable installer that I could find. Where is it supposed to be? If it's not there, then what?
Thanks,

I'll try to be more clear. In the Feisty CD I burned from .iso, there is an INSTALL folder. In that folder are the following files:
  boot.msg
  ofboot.b
  pegasos
  udeb.list
  yaboot
  yaboot.conf

The pegasos icon is the only one that looks like a terminal icon (the others look like text file icons). Following is what's in pegasos, and I'm not very terminal savvy:

  \ FORTH is identifed by a forth comment at first line
\
\ terminal control stuff
\
: TTY.CSI d# 27 EMIT ASCII [ EMIT ;
: TTY.HOME    TTY.CSI ASCII H EMIT ;
: TTY.CLR_EOS TTY.CSI ASCII J EMIT ;
: TTY.HOME_CLR TTY.HOME TTY.CLR_EOS ;
\
\ boot menu stuff
\
: my-max-boot-num 3 ;
: my-boot-default 1 ;
: my-boot-delay d# 300 ; \ unit = 100 ms
: my-print-menu ( -- )
  TTY.HOME_CLR
  ."  "                                    			cr
  ." Welcome to Ubuntu feisty!"			cr
  ." "								cr
  ." This is an Ubuntu installation CDROM,"		cr
  ." built on 20070417."					cr
  ." "								cr
  ." The default option is (1) 'install'. For maximum"		cr
  ." control, you can use the (2) 'expert' option."		cr
  ." "								cr
  ." ************************************"			cr
  ." If in doubt, just choose (1) 'install'"			cr
  ." ************************************"			cr
  ."  "								cr
  ." 1: install"   						cr
  ." 2: expert"   						cr
  ." 3: return to OF prompt"					cr
  ."  "								cr
;
: my-boot-case ( num -- )
  ."  " cr
  case
    1 of " cd install/powerpc/vmlinuz-chrp.initrd --" endof
    2 of " cd install/powerpc/vmlinuz-chrp.initrd priority=low --" endof
    3 of " none" endof
  endcase
  $boot
;
: my-input-num ( wait-period max-boot-num default-num -- boot-num )
  1 \ loop-inc = 1
  3 pick 0 do
    0d emit
    ." press 1-"
    ( wait-period max-boot-num default-num loop-inc )
    2 pick ascii 0 + emit
    dup 1 = if
      ."  within "
      3 pick i - d# 10 / .d
      ."  seconds"
    then
    ."  (default: "
    over ascii 0 + emit
    ." ) :                   "
    d# 100 ms
    key? if
       key
       ( wait-period max-boot-num default-num loop-inc key )
       dup 0d = if \ return pressed
         drop leave
       then

       ascii 0 -
       ( wait-period max-boot-num default-num loop-inc num )
       dup 1 5 pick
       ( wait-period max-boot-num default-num loop-inc num num 1 max-boot-num )
       between if
         rot drop swap leave
       then

       ( wait-period max-boot-num default-num loop-inc num )
       2drop 0  \ loop-inc = 0
    then
  dup +loop
  drop
  ( wait-period max-boot-num boot-num )
  nip nip
;


my-print-menu
my-boot-delay my-max-boot-num my-boot-default my-input-num
my-boot-case

---

### Post by pxwpxw on 2007-08-20
You have to boot from the CD and wait till it starts up a Ubuntu desktop with an install icon.
Start up with the CD in the slot while holding down the C key, and it should all happen.
If you knew all that, well I got the wrong problem.

---

