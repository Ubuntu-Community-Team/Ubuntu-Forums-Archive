---
title: "Internet Connection Failing"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Sabar on 2007-03-31
Hello everyone.

I am currently running Firefox.  and checking out the forums. Unfortunately when I try to go to a different web site I get this error.

> 
The connection has timed out
The server at [www.google.com](www.google.com) is taking too long to respond.
   *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.



So far I haven't been able to go anywhere non Ubuntu. Don't know if this is by design or flaw. 

Even searching around the Forums here, my browser seems Very very slow sometimes.  I know this isn't much information to go on but does anybody have any idea what it could be?

On a side note. does anyone know how to get a Logitech mouse Mx700 to work properly? Currently the basic mouse features work on it. trying to get my buttons to work on it though.

Thanks every one
Sabar   
:guitar: 

p.s. foot note I am running on a DSL service here. Currently I am downloading a packet and it is coming in at 32 - 34 Kb/s is this what I should be expecting? Thanks again

---

### Post by SoggyCornflake on 2007-03-31
I have had a similar problem and posted the same kind of thing.

I got a reply that linked me to this [thread]("http://www.ubuntuforums.org/showthread.php?t=87798").

I did make the change and I think that may have solved the problem.  I hope it does for you.

I did find that KDE's Konqueror was able to browse without timing out.  In fact, often I'd try to open a website in Firefox.  When it would time out, I'd open it in Konqueror without problem.  Then if I tried to open it with Firefox it would pop right up - no problem.  It was as if Konqueror acted like an icebreaker for Firefox if you get my drift.

Anyway since making the change oulined in the linked thread, I haven't had to do my Konqueror - Firefox switching trick.

I hope it works for you.  If not, hopefully somebody who's got loads of beans will know what's really the problem.

---

### Post by Sabar on 2007-03-31
Thanks for the reply Soggycornflakes.

The only concern I have is the post by Yagisan. The last paragraph has in it 

> One thing you can try is, with IPv6 enabled, to launch a terminal, and
type 'host www.google.com'. If the command succeeds quickly, listing
Google's IPs, then you're not having general network connectivity
trouble, and you can start filing bug reports against whichever specific
applications are being slow.

I tried this. Yep even found the terminal on my own and all, and I very quickly got a response saying 
> 
[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com) has address 216.239.37.104
[www.l.google.com](www.l.google.com) has address 216.239.37.99
;; Warning: Message parser reports malformed message packet.
[www.google.com](www.google.com) is an alias for [www.l.google.com](www.l.google.com).


That popped up almost instantaneous. so not sure what route to follow. 

For you gurus out there that know allot about what your talking about. Please keep in mind some of us ( ME!! ) are way over our heads here. so info like what I am about to quote doesn't help me.

> cd /etc/modprobe.d
darwinhwebb@Celcila-24:/etc/modprobe.d$ dir
aliases alsa-base blacklist isapnp
aliases~ arch bluez nvidia-kernel-nkc
aliases.dpkg-old arch-aliases ibm_acpi.modprobe toshiba_acpi.modprobe
darwinhwebb@Celcila-24:/etc/modprobe.d$ cat aliases
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ################################################## ########
alias net-pf-1 unix
alias net-pf-2 ipv4
alias net-pf-3 ax25
alias net-pf-4 ipx
alias net-pf-5 appletalk
alias net-pf-6 netrom
alias net-pf-7 bridge
alias net-pf-8 atm
alias net-pf-9 x25
# 1, 2, 3 new lines
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ivp6 off
#alias net-pf-10 ivp6 =========the original line
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
Reply With Quote

I don't even know where to find it. please keep in mind not to always skip the first step or two that EVERY ONE SHOULD KNOW. some of us ( ME!) don't even know enough of the basics. personally I am just feeling lucky I got it on my computer. :) 

Thanks for everyone's help I am sure dealing with Noobs can be a pain.
Sabar
:guitar:

---

### Post by Sabar on 2007-04-01
Fixed it! Maybe?

Found a post that had this info on it

> Disable IPv6 in Firefox

In your browser address window type:

about:config

scroll down untill you see something like network dns IPv6 ... Click on it and it should say "True"

Restart Firfox and see if that help. 

This just disables in Firefox not system wide.

Specifically in mine it said  "Network dns Disable IPv6"  under the value column it said "false" I double clicked the line changing it to "TRUE" 

Thanks For the posts guys 
Sabar

:)

---

### Post by Sabar on 2007-04-02
Logitech Mx700 fix

[I actually got it to work!]("http://www.ubuntuforums.org/showthread.php?t=399374")

Sabar

---

