---
title: "Green [ ok ] messages"
date: 2004-12-18
forum: Art &amp; Design
---

### Post by rasher on 2004-12-18
I was annoyed that during boot, only the status messages showing [fail] got coloured (red), so I created a very simple patch that makes the [ ok ] messages appear in green.

The patch applies to /lib/lsb/init-functions

```
--- init-functions.orig 2004-12-18 23:45:08.756780424 +0100
+++ init-functions      2004-12-18 23:44:52.699221544 +0100
@@ -190,9 +190,10 @@
         END=`$TPUT hpa $COL`
         START=`$TPUT hpa 0`
         RED=`$TPUT setaf 1`
+       GREEN=`$TPUT setaf 2`
         NORMAL=`$TPUT op`
         if [ $1 -eq 0 ]; then
-            echo "$UP$END[ ok ]"
+            echo "$UP$END[ ${GREEN}ok${NORMAL} ]"
         else
             echo -e "$UP$START $RED*$NORMAL$END[${RED}fail${NORMAL}]"
         fi
```
I'm not at all sure this belongs in "Ubuntu Screenshots / Art Talk", but I figured it was about making Ubuntu pretty, and I didn't know where else to put it.

---

### Post by oddabe19 on 2004-12-18
> **rasher]I was annoyed that during boot, only the status messages showing [fail] got coloured (red), so I created a very simple patch that makes the [ ok ] messages appear in green.

The patch applies to /lib/lsb/init-functions

```
--- init-functions.orig 2004-12-18 23:45:08.756780424 +0100
+++ init-functions      2004-12-18 23:44:52.699221544 +0100
@@ -190,9 +190,10 @@
         END=`$TPUT hpa $COL`
         START=`$TPUT hpa 0`
         RED=`$TPUT setaf 1`
+       GREEN=`$TPUT setaf 2`
         NORMAL=`$TPUT op`
         if [ $1 -eq 0 ] said:**
> "
+            echo "$UP$END[ ${GREEN}ok${NORMAL} ]"
         else
             echo -e "$UP$START $RED*$NORMAL$END[${RED}fail${NORMAL}]"
         fi
```
I'm not at all sure this belongs in "Ubuntu Screenshots / Art Talk", but I figured it was about making Ubuntu pretty, and I didn't know where else to put it.


I know what you're talking about, and how to apply it, but howabout explaining how to apply the patch for those that don't know.

---

### Post by Smash on 2004-12-25
I think he would like to say to remove lines that starts with -, and add lines that starts with +.

Iive not already tried.

Good tip.
TNX

---

### Post by Rotarychainsaw on 2004-12-25
oops, i didnt take out the minuses but it still works.

---

### Post by fng on 2005-01-08
This patch should be default in ubuntu.

---

### Post by maart on 2005-01-09
What are other possible colors to use?

---

### Post by zeroK on 2005-01-09
[QUOTE=fng]This patch should be default in ubuntu.[/QUOTE]
 Yeah, I was thinking exactly the same thing right after booting Ubuntu for the first time. Thanks rusher :-)

---

### Post by shimon on 2005-01-10
[QUOTE=fng]This patch should be default in ubuntu.[/QUOTE]
 yes another distros have it

but uslpash will hide this patch

---

### Post by heema on 2005-01-10
Yeah thanks , as i have been used to seeing the OK green   

it gives me a good feeling that everything is working right  :smile:

---

### Post by Device on 2005-01-10
[QUOTE=oddabe19]I know what you're talking about, and how to apply it, but howabout explaining how to apply the patch for those that don't know.[/QUOTE]
patch -p0 < /path/to/this/patch

---

### Post by shimon on 2005-01-11
<HostingGeek> Green [ ok ] messages? why not apply this patch by default like all other distros have?
<HostingGeek> [http://ubuntuforums.org/showthread.php?t=8556](http://ubuntuforums.org/showthread.php?t=8556)
<fabbione> it has been discussed on the mailing list iirc
<fabbione> because it is a communityu decision done by all users
<fabbione> therefor discussed between all of them
<fabbione> and the verdic was something like: no thanks
<fabbione> for different reasons
<mjt> "quiet" graphical boot, green/red messages.. and a cup of coffee every morning pls. ugh.
<HostingGeek> link
<HostingGeek> i need to join more mailing lists
<Keybuk> fundamantally, colour should only be used to highlight problems
<Keybuk> in particular, that's a very silly patch -- the green and red are of the same intensity, so a colour blind person wouldn't see any difference
<Keybuk> by using red for fail, they stand out in the otherwise black/white boot sequence
<Treenaks> make it BLINK
<Treenaks> that's stand out for sure!
* Keybuk shakes his head
<Keybuk> it'll be colour prompts next
<Treenaks> Keybuk: Ubuntu needs more gentoo influence :P
--> Gorth (~Gorth@cpe.atm2-0-51110.0x50a4d38e.abnxx10.customer.tele.dk) has joined #ubuntu-devel
<Keybuk> we had gentoo influence for warty
* Mithrandir whacks Treenaks 
<bob2> next you'll all be madly trying to get the boot time down to < 30 seconds

---

### Post by doobiest on 2007-04-11
has anyone found out how to do this for newer versions? Feisty? I cant figure it out, the init-functions file is much different.

---

### Post by oktubr3 on 2008-09-16
For Ubuntu Hardy Heron: [http://www.drfest.com.ar/2008/09/howto-arranque-de-ubuntu-804-sin.html](http://www.drfest.com.ar/2008/09/howto-arranque-de-ubuntu-804-sin.html)

---

### Post by cdsboy on 2008-09-18
> **shimon said:**
> 
<bob2> next you'll all be madly trying to get the boot time down to < 30 seconds

A little off topic but... my boot time is 26 seconds xD

---

### Post by dantata on 2009-07-20
How does this (green OK) work in Jaunty? For instance, there is no *echo "$UP$END[ ok ]"* line?

Thanks.

---

### Post by Labello on 2009-07-21
> **cdsboy said:**
> A little off topic but... my boot time is 26 seconds xD

not that fast, but depends on your machine ;-)

> **dantata said:**
> How does this (green OK) work in Jaunty? For instance, there is no *echo "$UP$END[ ok ]"* line?

Thanks.

I was also wondering how to achieve that with jaunty... ame problem here ;)

---

### Post by mcduck on 2009-07-23
Edit /etc/lsb-base-logging.sh, then change the echo "[ OK ]" in line 136 (under the log_to_console log_end_msg -line) to this:

```
printf '[ '
$TPUT setaf 2 # green
printf OK
$TPUT op # normal
echo ' ]'
```

---

### Post by razorboy5 on 2009-07-23
sry very noob at Ubuntu

could u explain how to apply this patch again?

i opened up the file specified ( see alot of words and codes )

do i just copy the code on there?

thx

---

### Post by dantata on 2009-07-24
> **mcduck said:**
> Edit /etc/lsb-base-logging.sh, then change the echo "[ OK ]" in line 136 (under the log_to_console log_end_msg -line) to this:

```
printf '[ '
$TPUT setaf 2 # green
printf OK
$TPUT op # normal
echo ' ]'
```

Thanks. Worked like a charm.

---

### Post by Labello on 2009-07-24
> **dantata said:**
> Thanks. Worked like a charm.

+1

confirmed

---

### Post by razorboy5 on 2009-07-26
ok +2 for confirmed :P thx

however the OK button doesn't show during boot but shows on shutdown

is that normal? i'm on 9.0.4 jaunty Ubuntu

---

### Post by Gourgi on 2009-07-26
> **mcduck said:**
> Edit /etc/lsb-base-logging.sh, then change the echo "[ OK ]" in line 136 (under the log_to_console log_end_msg -line) to this:

```
printf '[ '
$TPUT setaf 2 # green
printf OK
$TPUT op # normal
echo ' ]'
```

thanks!
nice tip

---

