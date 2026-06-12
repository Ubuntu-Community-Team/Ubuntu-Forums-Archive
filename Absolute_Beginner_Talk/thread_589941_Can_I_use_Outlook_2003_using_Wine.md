---
title: "Can I use Outlook 2003 using Wine?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by RichTJ99 on 2007-10-24
Hi,

I am using Exchange 2007 for my email & Outlook 2003 on  my WinXP machine.  I am looking to move over the Ubuntu but the lack of email support for exchange isnt so great.  I know about evolution but its not really as seamless as I would like.  

I dont know much about Wine except that it somehow magically lets you run windows applications in Linux.  

I suppose that using VMWare is another option, but i would like to stick as natively as possible to Ubuntu.

So, with that being said, is this possible?

Thanks,
Rich

---

### Post by ByteJuggler on 2007-10-24
Probably not, see [here]("http://appdb.winehq.org/appview.php?iVersionId=2526").  VMWare would probably be your only option if you want to stick to Outlook, until such time as Wine supports it.  That  said, the test is a couple of months old, so it might be possible that it works by now.  I might have a go later and if so I'll report back.

---

### Post by brinux on 2008-04-16
Just tested Outlook 2003 myself.  It **installs** fine in Wine (version 0.9.59).  (Joy!)

*However*, when attempting to run it, it claims it needs Internet Exploder v. 4.01 or greater to run.   (weeping)

I figured I'd install IE4.01 to solve that (found a copy of 4.01 here  [http://www.oldversion.com/program.php?n=msie]("http://www.oldversion.com/program.php?n=msie") ) I thought 4.01 would be best because it would not need dot net, nor would it install very much on my system..... however, that install wants to install animated cursors, which wine doesn't support. drat.

I'm still hoping that Evolution starts supporting Exchange 2007 soon myself, as OWA is currently my only alternative, and that's a *very* poor alternative.

---

### Post by pedantic-steve on 2008-04-16
I need outlook and the rest of MS Office for work so it was a deal breaker for me.

I forked over 39 bucks to codeweavers for crossover office. It was the best 39 bucks I ever spent!  Crossover installs office 2003 flawlessly.  It will also install IE 6 as well if you need to use IE for certain web apps. 

I currently use outlook and the rest of the office 2003 suite under Ubuntu 7.10 with no problems. 

I am sure it installs under the standard (non-crossover) WINE but I didnt want to mess with all the WINE configurations so for me Crossover was a better choice for me than standard WINE.

-Steve

---

### Post by bm13084 on 2008-04-16
why dont you use thunderbird?

i use thunderbird portable with wine so i can use it on any of my computers...

---

### Post by pedantic-steve on 2008-04-16
> **bm13084 said:**
> why dont you use thunderbird?

i use thunderbird portable with wine so i can use it on any of my computers...

I need exchange support.  I know Evolution supports Exchange to some extent but not fully.   I can connect to the OWA interface or through MAPI with Evolution but I need to be able to archive my exchange folder locally when I get near my quota which I cannot find out how to do in Evolution.

Also, I need Word for some templates I use for work. They have specific macros in them that do not work in open office.

Some work web applications I use also require Internet Explorer/Active X so that was a necessity as well.   

When the day comes that I do not need any of the above applications I will not hesitate to drop them... but for the time being they are a necessary evil if I am going to use Linux.  Running them in WINE/Crossover means I don't need to dedicate any resources to a virtual machine.  

-Steve

---

### Post by stchman on 2008-04-16
Evolution is a great Outlook clone and comes with Ubuntu by default.  Evolution even supports Exchange servers.  If you have used Outlook, you will be at home using Evolution.

I find that while Outlook being a great email program is bloated.  Evolution rocks.

---

### Post by pedantic-steve on 2008-04-16
> **stchman said:**
> Evolution is a great Outlook clone and comes with Ubuntu by default.  Evolution even supports Exchange servers.  If you have used Outlook, you will be at home using Evolution.

I find that while Outlook being a great email program is bloated.  Evolution rocks.

I agree, Evolution is very intuitive and responsive.  I had it set up and had no problems getting my email or viewing my exchange calendar.  

the problem is I need to "archive" my email every couple of weeks due to my email quota.  I did not find an easy way to do this in Evolution. 

Also, the Evolution in Hardy (2.22) does not work with the exchange server my company has (I think it is exchange 2007) due to the server not supporting the higher version of TLS implemented in Gnome 2.22.  I did get it to work in Gutsy (which I am still using) but still have the problem mentioned above with archiving.  For me, the best solution was to use Outlook.  When Gnome 2.24 is released I will take a look at the improved exchange capabilities in Evolution.

-Steve

---

### Post by stchman on 2008-04-16
> **pedantic-steve said:**
> I agree, Evolution is very intuitive and responsive.  I had it set up and had no problems getting my email or viewing my exchange calendar.  

the problem is I need to "archive" my email every couple of weeks due to my email quota.  I did not find an easy way to do this in Evolution. 

Also, the Evolution in Hardy (2.22) does not work with the exchange server my company has (I think it is exchange 2007) due to the server not supporting the higher version of TLS implemented in Gnome 2.22.  I did get it to work in Gutsy (which I am still using) but still have the problem mentioned above with archiving.  For me, the best solution was to use Outlook.  When Gnome 2.24 is released I will take a look at the improved exchange capabilities in Evolution.

-Steve

Exchange 2007?  Got to love M$ proprietary formats.  I will take a POP server for my email as EVERY email program supports it.

---

### Post by ByteJuggler on 2008-04-17
> **brinux said:**
> Just tested Outlook 2003 myself.  It **installs** fine in Wine (version 0.9.59).  (Joy!)

*However*, when attempting to run it, it claims it needs Internet Exploder v. 4.01 or greater to run.   (weeping)

I figured I'd install IE4.01 to solve that (found a copy of 4.01 here  [http://www.oldversion.com/program.php?n=msie]("http://www.oldversion.com/program.php?n=msie") ) I thought 4.01 would be best because it would not need dot net, nor would it install very much on my system..... however, that install wants to install animated cursors, which wine doesn't support. drat.

I'm still hoping that Evolution starts supporting Exchange 2007 soon myself, as OWA is currently my only alternative, and that's a *very* poor alternative.

You can in fact install later versions of IE using Wine!  See [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page").

---

### Post by Trail on 2008-04-17
What do you mean archive your email due to quota?!!

First of, you can download a local copy of the email and store it on your PC, and discard the copy that the server has. Then, you can additionally backup those local copies easily. I think any client would support that. Evolution certainly does.

---

### Post by pedantic-steve on 2008-04-17
> **Trail said:**
> What do you mean archive your email due to quota?!!

First of, you can download a local copy of the email and store it on your PC, and discard the copy that the server has. Then, you can additionally backup those local copies easily. I think any client would support that. Evolution certainly does.

hmm, I didn't see that option but to be honest I didnt give it much time due to the fact I needed to get my mail up rather quickly.  I did see an option to "download for offline use" but couldn't find where it actually stores it.  I was looking for a way to take the mail and move it to the "on this computer" inbox that I removed from the server from the exchange account.

To be honest, it that process is relatively straightforward (and I just missed the option in the menus) then I will give Evolution another go.  In fact, it is still configured for my mail at the moment.  

-Steve

---

### Post by Trail on 2008-04-18
It saves the stuff on ~/.evolution if I remember correctly. The backing up option (to a tarball; which by the way can be imported to Kmail and the like nicely) is a regular menu entry and automatic.

I find it pretty straightforward; you should give it a look sometime.

---

### Post by pete on 2008-04-28
> **Trail said:**
> It saves the stuff on ~/.evolution if I remember correctly. The backing up option (to a tarball; which by the way can be imported to Kmail and the like nicely) is a regular menu entry and automatic.

I find it pretty straightforward; you should give it a look sometime.
Trail, it works somewhat differently when Evolution is connected to an Exchange account.  All of the mail *is* stored in ~/.evolution, but it's *also* stored in the user's account on the Exchange server.  It's not like a POP3 account where you can tell your client to download the messages and delete them from the server.

Pedantic-Steve, the only method I've found to stay under quota (aside from wholesale deletion of message) is to manually move folders/messages from my Exchange account folder in Evolution to the "On This Computer" folders.

---

### Post by pedantic-steve on 2008-05-03
> **pete said:**
> 
Pedantic-Steve, the only method I've found to stay under quota (aside from wholesale deletion of message) is to manually move folders/messages from my Exchange account folder in Evolution to the "On This Computer" folders.

Thanks Pete, That is what I thought was happening since my "over the quota" messages kept coming in.  

Perhaps in a future version Evolution will contain the "archive" feature similar to Outlook.  It would certainly make it easier to switch in an exchange environment.

-Steve

---

### Post by tact on 2008-05-05
> **pedantic-steve said:**
> 
the problem is I need to "archive" my email every couple of weeks due to my email quota.  I did not find an easy way to do this in Evolution. 
-Steve

There is no auto-archive as in outlook so what I did is to create folders like "Archive Inbox" and "Archive Sent Mail" in the "On This Computer" section in evolution.

Then when its time to clear stuff from my exchange account I "move" as many mails as I want from (eg) exchange server Inbox to "Archived Inbox" on the local computer.

It takes a while if you have a slow connection and also because its doing all the work via the OWA link to exchange server.  But it works.

---

### Post by pedantic-steve on 2008-05-18
> **serobb said:**
> Hey, 

Why dont you guys this: 

It worked for me :)

I am using that.  However I purchased it from codeweavers and did not download it from piratebay.

---

### Post by emptycup on 2008-05-26
Hi all,

I just installed Ubuntu today.  I am using a dual boot setup between Vista and Ubuntu.  In the methods discussed in this thread is it possible to install Outlook 2003 in Ubuntu and share the same PST file as the one in Vista?

Ideally I would like to be able to check my emails without manually  import/exporting emails that a receive when using one OS to another.

Thanks for any help you guys come up with!

---

### Post by ByteJuggler on 2008-05-26
> **emptycup said:**
> Hi all,

I just installed Ubuntu today.  I am using a dual boot setup between Vista and Ubuntu.  In the methods discussed in this thread is it possible to install Outlook 2003 in Ubuntu and share the same PST file as the one in Vista?

Ideally I would like to be able to check my emails without manually  import/exporting emails that a receive when using one OS to another.

Thanks for any help you guys come up with!

It's probably possible, but you'll have to try it.  You'd have to have 2 seperate installs of course, one on Vista, one on WINE, both configured to read/use the same pst file.  This should be possible.

---

### Post by muddyh2o on 2008-07-07
> **stchman said:**
> Evolution is a great Outlook clone and comes with Ubuntu by default.  Evolution even supports Exchange servers.  If you have used Outlook, you will be at home using Evolution.

I find that while Outlook being a great email program is bloated.  Evolution rocks.

i would PAY MORE for Evolution to work as well (or as poorly) as Exchange.

I have many old .pst files which i still need access to, and need to search against.

I need access to my shared Exchange calendar, on the Exchange server, and to see other users free/busy information.

I also need my contacts to persist on the server (Evolution doesn't sync them very well) and through to my mobile devices / OWA

I WANT to use something other than Outlook.  But I have no choice.  I'll be paying codeweavers...

---

### Post by HDave on 2008-07-14
Have to say I just tried the crossover way to run Outlook 2003 on Wine and it works just fine.  A little buggy, but not bad at all.

Will more than suffice until Evolution can talk native MAPI with Exchange 2007 Server.

---

