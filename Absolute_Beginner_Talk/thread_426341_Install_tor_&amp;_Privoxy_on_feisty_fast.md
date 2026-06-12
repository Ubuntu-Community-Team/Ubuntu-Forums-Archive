---
title: "Install tor &amp; Privoxy on feisty fast"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by bprof on 2007-04-28
Hi,

I'm not sure if this is the right section, my question is how can I install tor and Privoxy on Feisty fast?

I read many sites discussing it for older ubuntu, I have tried many methods but nono seems working.

Here is one place I tried its described method:

[http://ubuntu-tutorials.com/category/big-brother/](http://ubuntu-tutorials.com/category/big-brother/)

I tried this also:

apt-get install tor

Both didn't work.

Could you please help me?

Thank you,

---

### Post by satellite360 on 2007-04-29
```
sudo apt-get install tor privoxy
sudo gedit /etc/privoxy/config
```
Add the following line to the top of the config file (include the dot):
```
forward-socks4a / 127.0.0.1:9050 .
```
Restart Gnome (Ctrl + Alt + Backspace)
Install the [Torbutton plugin]("https://addons.mozilla.org/firefox/2275/")
Restart Firefox and enable Tor
Visit the [Nighteffect Tor Network Status]("https://nighteffect.us/tns/") page to test whether Tor is working.

---

### Post by bprof on 2007-04-30
Thanks for your help satellite360,

I have tried the commands you gave me, but it gave me the same error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tor
```

I'm not sure is causing this error (I'm new to ubuntu)

Thanks,

---

### Post by starcraft.man on 2007-04-30
You likely don't have the right repositories in your sources file.

[Here!]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")
That should get you having the right repositories to get tor, I assume its in universe or multiverse.
Make sure to get keys btw.

If your using an older version, find the same section in Edgy and Dapper.

---

### Post by bprof on 2007-05-03
> **starcraft.man said:**
> You likely don't have the right repositories in your sources file.

[Here!]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")
That should get you having the right repositories to get tor, I assume its in universe or multiverse.
Make sure to get keys btw.

If your using an older version, find the same section in Edgy and Dapper.

Could you please explain more on this?

I have tried to add a universe and multiverse, in both cases I wasn't able to install any package till I removed them.

I'm not sure as to how I can use repository, and in which one I can find tor.

Thanks,

---

### Post by starcraft.man on 2007-05-03
That will be 99 cents a line for a full explanation of the process :p

Just kidding ^^.

Easy enough, open up the terminal, Applications > Accessories > Terminal. In the terminal, type this: 

```
sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
```

Thats to back up your list you have now just in case, cp is the copy command, first is location of original, second is location of copy.

Then, you will type in to terminal.

```
sudo gedit /etc/apt/sources.list
```

This will open up the text editor.

Then, select everything in there and delete it. Then paste in the following.

```
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

Then, save the file and close.

Next in the terminal type:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

This gets you the key for the extra repos.

Then, the last thing you need to do is update.

```
sudo aptitude update
```

After that, all should work.

If any trouble post back :)

---

### Post by bprof on 2007-05-03
Thanks so much it worked it worked.

I should start learn these things this is my first experience with ubuntu and so far its great, I think I will soon say go away to MS :).

How much time did it take you to get where you are? (If you don't mind)

:popcorn: 

Again thanks a lot,

---

### Post by starcraft.man on 2007-05-03
> **bprof said:**
> Thanks so much it worked it worked.

I should start learn these things this is my first experience with ubuntu and so far its great, I think I will soon say go away to MS :).

How much time did it take you to get where you are? (If you don't mind)

:popcorn: 

Again thanks a lot,

No problem, glad to be of service. As for how long it took me to learn Ubuntu... less than 2 weeks, a month to pick up so that I was really comfortable with it. I've only been using Ubuntu since mid/late march. :)

I'm a long term windows power user, I'm used to picking stuff up quick :)

And your very welcome, feel free to ask more questions.

Also, check my sig link to ubuntu guide, great resource to learn.

---

### Post by bprof on 2007-05-03
```
No problem, glad to be of service. As for how long it took me to learn Ubuntu... less than 2 weeks, a month to pick up so that I was really comfortable with it. I've only been using Ubuntu since mid/late march. 
```

WOW thats amazing, I thought at least few months but 2 week you are a genius. I didn't work on Linux deeply before I just know the very basics, I hope I can be good in Ubuntu in 2 months :) that will be great.

```
And your very welcome, feel free to ask more questions.
```

Thank you so much for your help you solved 2 problems I had so far, in case I have more problems on the way I think I have a great source of help.

I will start reading ubuntu guide and see where I will go from there.

Thanks so much again!

---

### Post by sefs on 2007-05-04
Hi all, 

Is there a way to ensure that i use an american proxy in selected cases using tor+privproxy+torbutton?

I see that when I enable the torbutton it seems to randomly select proxies in various countries.  I've seen germany and sweden so far.

Thanks.

---

### Post by GaryH on 2007-05-06
Hi Everybody,

I've been experimenty with Privoxy and it appears to be working. In Swiftfox the Tor enable/disable icon shows in the lower right and it appears to respond properly to mouse click events. With Tor enabled, Ubuntu can't figure who I am immediately after login and surfing slows down. I presume  this is the correct behavior. One question remains however. What's supposed to happen when browsing [https://nighteffect.us/tns/](https://nighteffect.us/tns/)?

To All, thanks.

Peace,
GaryH

---

### Post by starcraft.man on 2007-05-06
> **sefs said:**
> Hi all, 

Is there a way to ensure that i use an american proxy in selected cases using tor+privproxy+torbutton?

I see that when I enable the torbutton it seems to randomly select proxies in various countries.  I've seen germany and sweden so far.

Thanks.

The way Tor works ensures that that is fundamentally random. The Onion Router is based on the principle that there is a network of interconnected computers acting as servers all around the world. When you make a request for information on the network, you contact a first server, the server you contact is random and cannot be selected. That server then "wraps" your request for information with its IP, it basically makes it so that the next hop willl only know that it came from that server. Thusly, think of it like this, each hop forward is like adding a skin layer to an onion, and at each step only the previous hop is known to the next, and more importantly each hop is inherently random, you'd likely NEVER take the exact same path to your information.

If you do however want to have an American IP, say that there is a show on the sci fi channel who has stupid executives and a wonderful cast and production team, and they put certain episodes up on the net and make it only for american IPs, then you can't use tor. You need a one stop Proxy. Google for an american proxy server and you should find one.

---

### Post by starcraft.man on 2007-05-06
> **GaryH said:**
> Hi Everybody,

I've been experimenting with Privoxy and it appears to be working. In Swiftfox the Tor enable/disable icon shows in the lower right and it appears to respond properly to mouse click events. With Tor enabled, Ubuntu can't figure who I am immediately after login and surfing slows down. I presume  this is the correct behavior. One question remains however. What's supposed to happen when browsing [https://nighteffect.us/tns/](https://nighteffect.us/tns/)?

To All, thanks.

Peace,
GaryH

Yup, you are probably set up correctly, Tor servers are for the most part slower than surfing normally, if only for the reason they have to make so many jumps, but I am sure they are very busy and there are only so many volunteers.

I don't know what the site is supposed to do, can you elaborate?

and To bprof: I'm sure you'll pick up Ubuntu fast :) I'll be around if ya got any more questions.

---

### Post by sefs on 2007-05-07
> **starcraft.man said:**
> erican IP, say that there is a show on the sci fi channel who has stupid executives and a wonderful cast and production team, and they put certain episodes up on the net and make it only for american IPs, then you can't use tor. You need a one stop Proxy. Google for an american proxy server and you should find one.

Exactly what I wanted and also you made me grin.

I was doing a little research and apparently you can have your cake and eat it too...or this is what I am made to understand.

In the privoxy config file.... you can set up the socks fowards.  One of which is for all target urls foward them thru the tor socks service with out any parent proxy like so,

forward-socks4a / localhost:9050 .

In there documentation they allude to the point that you can have a list of these and privoxy just sequentially goes thru the list until it finds a match...as an example....


forward-socks4a / localhost:9050 .
forward-socks4a *.scifichannelwithstoopidexecs.com localhost:9050 amercianproxy.com:80


and what is suppose to happen as i read from the docs is that it would go thru tor...but the tor exit node will then foward all request for scifichannelwithstoopidexecs.com domains to the american proxy as the last hop.

Giveing you the benefits of tor...but with the cherry of exiting at a proxy of choice.

i was look for where i found that but can't seem to find the url. 

However it dosn't seem to work as they say, at least not for me.

---

