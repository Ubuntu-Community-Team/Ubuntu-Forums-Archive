---
title: "Certain web pages will not load"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by CRuckis on 2007-07-20
Hey, I know I've seen a lot of threads about this, but they don't seem to help my problem.

Majority of the sites I access work fine, but in the case, one site i visit frequently is giving me some problems,

This site and (all the links from it that I have tried) are not working:

[http://www.binghamton.edu](http://www.binghamton.edu)
[http://busi.binghamton.edu](http://busi.binghamton.edu)
[http://smail.binghamton.edu](http://smail.binghamton.edu)

Just a few of the many links from that site I have tried. I have already changed "Ubuntu-feisty" to "ubuntu-7.04" in FF's "about:config"

Any ideas?

---

### Post by Freddy on 2007-07-20
Don't they load at all or is it just a rendering problem? You have all the plugins that these pages using installed.

My Firefox have no problem with those pages.

---

### Post by pbaehr on 2007-07-20
The pages look pretty straightforward. Is there an error message or just a blank page?

Could there be a problem resolving the domain name? What happens if you try to go to: 128.226.1.11 instead?

---

### Post by CRuckis on 2007-07-20
Entering the IP address has the same effect, the progress bar will go about half way, then it will never load, it just stalls there.

When I open "http://www.binghamton.edu" in a new window, the status bar says:

"Waiting for www.binghamton.edu..." and the progress bar is empty. Never loads.

---

### Post by pbaehr on 2007-07-20
Do you have another computer on the same network you can try? Or even just another browser?

While we wait for someone to jump in with a command for you to paste in the terminal to fix everything I'm just trying to narrow it down and find out if it's a firefox problem, an ubuntu problem, or a network problem.

Also, out of curiousity, what happens when  you ping the site?
```

ping binghamton.edu

```

---

### Post by CRuckis on 2007-07-20
> **pbaehr said:**
> Do you have another computer on the same network you can try? Or even just another browser?

While we wait for someone to jump in with a command for you to paste in the terminal to fix everything I'm just trying to narrow it down and find out if it's a firefox problem, an ubuntu problem, or a network problem.

Also, out of curiousity, what happens when  you ping the site?
```

ping binghamton.edu

```

Yes, actually I don't know how my network actually works, but it does. I have a dell desktop running XP which is connected to a linksys wireless card. I have an ethernet cable connected from that dell to this laptop, running only ubuntu feisty. The network just worked by itself, it said it connected through the wired network, I'm guessing ICS is turned on with the Dell.

I tried to access those sites through the dell and another dell laptop connected to the same network, both work.

Sorry, very new to linux and ubuntu, i'm guessing I put the ping code into terminal?

---

### Post by pbaehr on 2007-07-20
Yes, put the ping command in the terminal.

It will send a series of "pings" to the server and the server should respond. Once you've got a few press "ctrl+c" and it will stop and give you a report. If it was successful (the server responded to the requests) it will look something like this:
```

PING binghamton.edu (128.226.1.11) 56(84) bytes of data.
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=1 ttl=243 time=54.0 ms
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=2 ttl=243 time=52.2 ms
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=3 ttl=243 time=52.1 ms

--- binghamton.edu ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2020ms
rtt min/avg/max/mdev = 52.147/52.797/54.003/0.853 ms

```

---

### Post by CRuckis on 2007-07-20
My mistake, here it is:


```
chris@sidewinder:~$ ping binghamton.edu
PING binghamton.edu (128.226.1.11) 56(84) bytes of data.
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=1 ttl=241 time=32.1 ms
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=2 ttl=241 time=32.8 ms
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=3 ttl=241 time=33.5 ms
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=4 ttl=241 time=31.1 ms
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=5 ttl=241 time=33.0 ms

--- binghamton.edu ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 31.174/32.558/33.520/0.842 ms
chris@sidewinder:~$
```

---

### Post by pbaehr on 2007-07-20
No, that looks OK. Press "ctrl+c" (if it's still running) and you should see "0% packet loss" which means that every packet you sent was received and the server responded succesfully.

I would guess this means it's specifically a problem with firefox. At least we've narrowed it down.

EDIT: By the way, I guess next time I should specify something along the lines of
```

ping -c3 binghamton.edu

```

That will stop it after three tries. I just use ctrl+c to break out because I'm too lazy to type an extra two letters.

---

### Post by por100pre1 on 2007-07-20
Are you using any addons? Which ones if any?

---

### Post by CRuckis on 2007-07-20
> **pbaehr said:**
> No, that looks OK. Press "ctrl+c" (if it's still running) and you should see "0% packet loss" which means that every packet you sent was received and the server responded succesfully.

I would guess this means it's specifically a problem with firefox. At least we've narrowed it down.

Yeah I edited my post. I didn't really think this was a problem with ubuntu. Any Ubuntu-compatible browsers you recommend trying? Maybe a different browser will work, although I would prefer firefox. The other computers on the network load the site with firefox fine.

Edit:

When I go to 'Tools->addons' firefox says that I have no addons or themes installed, which should be accurate I don't recall every installing any.
The only plugin I recall downloading is flash.

PS - thanks for the terminal tip :D

```

chris@sidewinder:~$ ping -c3 binghamton.edu
PING binghamton.edu (128.226.1.11) 56(84) bytes of data.
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=1 ttl=241 time=34.5 ms
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=2 ttl=241 time=33.2 ms
64 bytes from bingnet1.cc.binghamton.edu (128.226.1.11): icmp_seq=3 ttl=241 time=36.0 ms

--- binghamton.edu ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 33.200/34.600/36.004/1.164 ms
chris@sidewinder:~$ 
```

---

### Post by pbaehr on 2007-07-20
Firefox should work fine. There's got to be a reason it's not working in this instance, but I can't figure it out. Do you know if you running the i386 version of Feisty or the amd64 version? I had a similar problem with the amd64 version which (now that you mention it) had to do with a badly configured Flash plugin. However, the 32 bit Flash is pretty reliable.

---

### Post by por100pre1 on 2007-07-20
Rename your~$ /.mozilla/firefox folder and restart firefox to see if it is a firefox setting issue.

---

### Post by CRuckis on 2007-07-20
No I'm running the i386 version, not the AMD.

Where is the /.mozilla folder and what should I rename it to?

---

### Post by larsa on 2007-07-20
I've the same problem. Using *Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.5) Gecko/20061201 Firefox/2.0.0.5 (Ubuntu-feisty)*.

The site I'd tried to load in Mozilla Firefox: [http://www.tromsfylke.no/](http://www.tromsfylke.no/) - wouldn't load, even with the "Rename your~$ /.mozilla/firefox folder and restart firefox to see if it is a firefox setting issue." - though, the same side worked perfectly fine with Mozilla Songbird.

Mozilla Firefox stop 'searching' after the page just after a few seconds, and give me the message: "The connection was reset".

Don't think that my extansions-list is so important, but here is it:
- Adblock Plus
- Download Statusbar
- Fasterfox
- Firebug
- FireFTP
- Foxytunes
- Tabbrowser Perferences

---

### Post by CRuckis on 2007-07-20
That's really funny, that site works for me. It's in a different language though.

---

### Post by por100pre1 on 2007-07-20
> **CRuckis said:**
> No I'm running the i386 version, not the AMD.

Where is the /.mozilla folder and what should I rename it to?

/home/yourusername/.mozilla/firefox/

any name will do by example firefox_backup

---

### Post by pbaehr on 2007-07-20
> **CRuckis said:**
> No I'm running the i386 version, not the AMD.

Where is the /.mozilla folder and what should I rename it to?

The .mozilla directory is in your home folder. The . before the name makes it hidden. Renaming it will force firefox to create a new set of preferences. Enter this in the terminal to do it:
```

mv ~/.mozilla/forefox ~/.mozilla/firefox_old

```

Then start firefox back up and see if it worked.

EDIT: I should mention while we're at it that "mv" is the move command (also used for renaming). We are telling the computer to move the folder ~/./mozilla/firefox to /.mozilla/firefox_old, in effect renaming it. Also, "~" is a shorcut for your home directory.

---

### Post by CRuckis on 2007-07-20
> **por100pre1 said:**
> /home/yourusername/.mozilla/firefox/

That was the first place I checked, it isn't there...maybe this is because firefox was installed on windows previously? This wouldn't make sense though because I'm pretty sure when I installed Ubuntu with the alternate disc I told it to format and use the entire drive. Once feisty was installed, firefox was already there.

---

### Post by pbaehr on 2007-07-20
> **CRuckis said:**
> That was the first place I checked, it isn't there...maybe this is because firefox was installed on windows previously? This wouldn't make sense though because I'm pretty sure when I installed Ubuntu with the alternate disc I told it to format and use the entire drive. Once feisty was installed, firefox was already there.

The dot before mozilla makes it a hidden folder.

---

### Post by por100pre1 on 2007-07-20
> **pbaehr said:**
> The .mozilla directory is in your home folder. The . before the name makes it hidden. Renaming it will force firefox to create a new set of preferences. Enter this in the terminal to do it:
```

mv ~/.mozilla/forefox ~/.mozilla/firefox_old

```

Then start firefox back up and see if it worked.

```

mv ~/.mozilla/firefox ~/.mozilla/firefox_old

```

Juzt and orthogrraphic corection ;)

---

### Post by pbaehr on 2007-07-20
Ah, good call. That command wouldn't have helped much.

---

### Post by mgmiller on 2007-07-20
You can't see the hidden files till you type ctrl-h then they will appear.  (hold down the control key and hit the letter h)  Otherwise, the command given above should work.  Just copy and paste it into a terminal.

---

### Post by CRuckis on 2007-07-20
Haha i picked up on it when terminal refused it. I tried this with no success. Bizarre.

---

### Post by pbaehr on 2007-07-20
Hm. I was really hoping por100pre1's idea would work.

Just look at all this stuff you're learning along the way, though. ; )

---

### Post by CRuckis on 2007-07-20
Oh, no, personally I kinda like this. Although it's very frustrating that I can't access that site, this is the only way I ever learn about things with computers lol. I tinkered around with windows so much that I became a pro, most of my knowledge came from forums. These ubuntu forums are by far the nicest and most helpful though :)

EDIT:

Should I try to change the "ubuntu-feisty" "ubuntu-7.04" tweak in about:config now that I have a fresh firefox running?

---

### Post by por100pre1 on 2007-07-20
As a workaround you can get Opera browser [here]("ftp://mirrors.evolva.ro/opera/linux/922/final/en/i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb"). It works fine.

---

### Post by pbaehr on 2007-07-20
I'm doing some research, take a look at this:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by CRuckis on 2007-07-20
> **por100pre1 said:**
> As a workaround you can get Opera browser [here]("ftp://mirrors.evolva.ro/opera/linux/922/final/en/i386/shared/opera_9.22-20070716.6-shared-qt_en_i386.deb"). It works fine.

Ok, let me try it out.

I just want to make a sidenote here. With all the troubles that comes with linux, i love it. **** windows.

---

### Post by por100pre1 on 2007-07-20
> **CRuckis said:**
> Oh, no, personally I kinda like this. Although it's very frustrating that I can't access that site, this is the only way I ever learn about things with computers lol. I tinkered around with windows so much that I became a pro, most of my knowledge came from forums. These ubuntu forums are by far the nicest and most helpful though :)

EDIT:

Should I try to change the "ubuntu-feisty" "ubuntu-7.04" tweak in about:config now that I have a fresh firefox running?

Don't think it will make any difference.

---

### Post by CRuckis on 2007-07-20
1. Tried doing that terminal fix - no dice

2. Changing the value in about:config - nuh uh

3. Now trying opera....

---

### Post by CRuckis on 2007-07-20
Well well well, gentlemen it appears that opera also does not like the binghamton.edu websites!

Edit:

Even when I add binghamton.edu to opera's "speed dial," the thumbnail never refreshes. It's just the loading circle over and over and over and over again.

---

### Post by pbaehr on 2007-07-20
Well, I guess that chucks the "it's firefox" theory out the window.

It's not a problem with resolving the address, since pinging binghamton.edu works. (So now that I think about it that ipv6 suggestion I posted before doesn't make sense)

I am sufficiently baffled.

---

### Post by CRuckis on 2007-07-20
As am I, I don't understand what else it can possibly be!

---

### Post by pbaehr on 2007-07-20
Obvious questions, but you don't have any software firewalls installed on the computer, right?

---

### Post by CRuckis on 2007-07-20
Only what came with Ubuntu, if it did, I don't even know haha. But no, I personally did not install any firewall, anti-virus, or anti-spyware...yet.

---

### Post by por100pre1 on 2007-07-20
No idea here. I can see those pages here without any problem... :(

---

### Post by CRuckis on 2007-07-20
Ahh, man. Maybe it has to do with how my network is set up?

This is so weird, it's driving me nuts. Not that it would make much of a difference since the Dell is set up to allow this laptop internet access, but I disaled all of the dell's firewall/anti-virus/anti-spyware programs. No change.

My next step would be to take the time to configure my wireless linksys card with Ubuntu, but I've read some of the forums and it looks like a real pain in the ***.

---

### Post by pbaehr on 2007-07-20
> **CRuckis said:**
> Ahh, man. Maybe it has to do with how my network is set up?

It doesn't seem like it. The other computers are working OK. Your settings seem right, too, since you can obviously browse other pages. Your computer is resolving the address properly, the ping was able to resolve fine. You're not running any firewall that would block it. I'm afraid I've exhausted all my possible solutions. Hopefully someone will come along with a better idea of what else it could be.

---

### Post by CRuckis on 2007-07-20
WOAH!

Ok, don't know what made me think of this, but I went to proxyfoxy.com and went to the binghamton.edu url through the proxy. It worked. the proxy messed up the page a bit, but at least it may be a clue to what's going on?

---

### Post by pbaehr on 2007-07-20
That was a good idea. I'm not entirely sure what it means, though.

What does this command output:
```

cat /etc/resolv.conf

```

---

### Post by CRuckis on 2007-07-20
Sorry I was at work. Let me try punching it in...

Edit:

Ok punching it into console yields this:

```
chris@sidewinder:~$ cat /etc/resolv.conf
search mshome.net
nameserver 192.168.0.1
chris@sidewinder:~$
```

---

### Post by CRuckis on 2007-07-21
Dammit, I still can't find a way around this problem! There are some more sites I found that won't work, and when I ping it in terminal I don't lose any packet data.

One of these sites is:

[www.citibank.com](www.citibank.com)  -> click on the login button on the top right, that page won't load for me.

---

### Post by CRuckis on 2007-07-21
NOT DEAD!! I Still need help!! lol

---

