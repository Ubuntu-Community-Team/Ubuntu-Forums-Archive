---
title: "[SOLVED] How to install TOR...maybe not?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-04-10
Sorry I keep nagging about TOR. I really can't get over it. Once more, here's what I did BOTH a couple of weeks ago (TORinstallation + use on Firefox = WORKED) and a few days ago (TOR installation: supposedly ok; use on Firefox: IT DOESN'T WORK).

IF ANYONE COULD PLEASE GET BACK ON THIS AND ADVISE, I'd be eternally grateful. Thanks tons (by the way, I'm on Ubuntu Gutsy + Firefox/2.0.0.13). Obviously I'm doing something wrong here (otherwise it wouldn't have worked the first time either, can I conclude?):  

1) *sudo apt-get install tor*
2) *sudo apt-get install privoxy*
3) *sudo nano /etc/privoxy/config*
4) add *forward-socks4a / localhost:9050 .* to the file */etc/privoxy/config*. Here's what the end part of my file looks like this: 

[I]#  the exit option on the File menu).
#
#close-button-minimizes 1

#  The "hide-console" option is specific to the MS-Win console version
#  of Privoxy.  If this option is used, Privoxy will disconnect from
#  and hide the command console.
#
#hide-console

#forward-socks4a / localhost:9050 .[/I]


5) modify the following part (same file, */etc/privoxy/config*) so that it looks like this: 

[I]#      The available debug levels are:
#
#          debug         1 # show each GET/POST/CONNECT request
#          debug         2 # show each connection status
#          debug         4 # show I/O status
#          debug         8 # show header parsing
#          debug        16 # log all data into the logfile
#          debug        32 # debug force feature
#          debug        64 # debug regular expression filter
#          debug       128 # debug fast redirects
#          debug       256 # debug GIF de-animation
#          debug       512 # Common Log Format
#          debug      1024 # debug kill pop-ups
#          debug      2048 # CGI user interface
#          debug      4096 # Startup banner and warnings
#          debug      8192 # Errors - *we highly recommended enabling this*
#[/I]

6) add "SafeLogging 1" to the file */etc/tor/torrc*. The end part of my file looks like this: 

[I]## users will be told that those destinations are down.
## 
#ExitPolicy accept *:6660-6667,reject *:* # allow irc ports but no more
#ExitPolicy accept *:119 # accept nntp as well as default exit policy
#ExitPolicy reject *:* # no exits allowed
#SafeLogging 1[/I]

7) run *sudo /etc/init.d/tor start*. Result: 

[I]sudo /etc/init.d/tor start
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
done.[/I]

8) run *sudo /etc/init.d/privoxy start*. Result: 
[I]
~$ sudo /etc/init.d/privoxy start
Starting filtering proxy server: privoxy.[/I]

9) run *netstat -a | grep 9050* (supposedly to check that everything's fine. Result: 

[I]~$ sudo /etc/init.d/privoxy start
Starting filtering proxy server: privoxy.
daniel@al:~$ netstat -a | grep 9050
tcp        0      0 localhost:9050          *:*                     LISTEN[/I] 

10) Go to Firefox>Edit>Preferences>Advanced>Settings and set it according to the screenshot here attached. 

11) Go to Firefox>Tools>AddsOn>Tor Button>Preferences>Use Custom Proxy Settings 

12) Install Tor Proxy Net toolbar. 

13) Restart the computer

14) test Firefox with "Tor Enabled" and "Tor Disabled" on the following websites (test's result):

a) [https://torcheck.xenobite.eu/](https://torcheck.xenobite.eu/) (message given on both "Enabled" and "Disabled": *Your IP is NOT identified to be a Tor-EXIT. So you are NOT using Tor to reach the web!*

b) [http://whatismyip.com](http://whatismyip.com) (IP address detected is the same on both "Enabled" and "Disabled". 

Notice that Tor Proxy Net toolbar works (by-passing blocked sites) regardless of whether or not Tor in enabled on Firefox. 

While writing this up it occurred to me it might be that "Tor Button" Firefox add-on is bugged/has some kind of issue on the Firefox version I'm using?

Also my assumption is that TOR Enabled should prevent (almost) anyone from detecting my IP address and TOR Proxy Net is specifically to surf blocked websites or the like. Is this correct?

At the moment, whether I've got TOR enabled or disabled, everyone can see my IP, but I can visit blocked sites. 

Thanks for taking the time to read this. Hope there's a solution.

---

### Post by al.adab on 2008-04-10
sorry I've realised the screenshot didn't upload. Here it is.

---

### Post by Sukarn on 2008-04-10
> **al.adab said:**
> 
#forward-socks4a / localhost:9050 .[/I]


Remove the # from the beginning of that line. You've got the forwarding disabled.

---

### Post by al.adab on 2008-04-10
Thanks Sukarn.

Now I can't reach any website (please see screenshot below) if TOR is enabled on Firefox. I understand that TOR slows down the connection, but then I'm again comparing it with my previous experience (when it worked): I was on the same connection speed, and it only took slightly longer to get to any website. Any idea?

---

### Post by hyperair on 2008-04-10
Looks like a DNS problem. Could you try pinging it?

---

### Post by al.adab on 2008-04-10
er...how do I "ping" it? :)

---

### Post by hyperair on 2008-04-10
```
ping www.xsmail.com
``` in the terminal.

---

### Post by al.adab on 2008-04-10
Here's what I get when I ping xsmail.com:

(TOR Enabled in Firefox)
[I]]$ ping [www.xsmail.com](www.xsmail.com)
PING [www.xsmail.com](www.xsmail.com) (66.111.4.56) 56(84) bytes of data.
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.56): icmp_seq=1 ttl=53 time=273 ms
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.56): icmp_seq=2 ttl=53 time=272 ms
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.56): icmp_seq=3 ttl=53 time=270 ms
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.56): icmp_seq=4 ttl=53 time=271 ms
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.56): icmp_seq=5 ttl=53 time=270 ms
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.56): icmp_seq=6 ttl=53 time=271 ms[/I]

(TOR Disabled in Firefox)
[I]~$ ping [www.xsmail.com](www.xsmail.com)
PING [www.xsmail.com](www.xsmail.com) (66.111.4.55) 56(84) bytes of data.
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.55): icmp_seq=1 ttl=53 time=255 ms
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.55): icmp_seq=2 ttl=53 time=255 ms
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.55): icmp_seq=3 ttl=53 time=238 ms
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.55): icmp_seq=4 ttl=53 time=238 ms
64 bytes from [www.fastmail.fm](www.fastmail.fm) (66.111.4.55): icmp_seq=5 ttl=53 time=248 ms[/I]

Does this help?

---

### Post by Locutus_of_Borg on 2008-04-10
I am using TOR + FoxyProxy with success and minimal to none configuration needed.  Of course this method only works in Firefox...

A bit unrelated, but I'm not sure exactly what it is you are wanting here.

---

### Post by hyperair on 2008-04-10
Yeah I think you should try using FoxyProxy. I didn't have that problem when using it. But it does look like Privoxy is having some sort of DNS resolution problem, though it doesn't show in ping.

---

### Post by al.adab on 2008-04-11
OK for FoxyProxy, could you tell me where to find it, how to install it, and if I need to get rid of Piroxy before installing it? Thanks!

---

### Post by hyperair on 2008-04-11
I'm not sure.. perhaps [http://addons.mozilla.org?](http://addons.mozilla.org?)

---

### Post by al.adab on 2008-04-11
thanks for your suggestion. I've installed FoxyProxy. I'm not sure I did the right thing when answering the initial setting questionnaire (in particular when I was asked if I still want to use TOR with Privoxy I clicked on "yes"). Anyway, could you please tell me what I should do to configure it?

---

### Post by hyperair on 2008-04-11
Try this: [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

---

### Post by al.adab on 2008-04-11
I had a look at it, but couldn't find any answer. Tor is installed. So is Privoxy and now FoxyProxy. If I have Tor enabled + FoxyProxy as "use proxy TOR for all URLs", I can't reach any site (I get the same  result as in the screenshot on this thread). If I have Tor enabled + FoxyProxy set as "use proxies on their pre-defined patterns...", I can navigate, however, if I test Tor on Xenobite, it tells me I'm not running TOR (see previous post on this thread). What to do?

A possible issue with DNS was mentioned. Also would it be possible to have a couple of screenshot  showing the ideal settings for FoxyProxy with Tor on Firefox? Any place where this is explained? Is there anything, in addition, I should do, like uninstalling Privoxy, or else?

---

### Post by hyperair on 2008-04-11
I'm really clueless at the moment. When I set TOR up, I just followed the instructions closely and everything worked nicely. If it didn't work for you then you must have messed up somewhere in the middle. The best thing I think you can do now is reinstall and purge all config files for TOR and privoxy. 
```
sudo apt-get install --reinstall --purge tor privoxy
```

---

### Post by al.adab on 2008-04-11
hyperair, what I did is shown on the first page of this thread. I did it once, and it worked. The second time (following a clean installation of gutsy) it didn't. I tried a third time + just run the command you gave, and it's still impossible to navigate with Tor enabled on Firefox. Do you know of anyone I could contact to solve what appears - to someone as ignorant of matters such as this - like a complete mystery?

---

### Post by al.adab on 2008-04-11
Update: I've uninstalled + reinstalled FoxyProxy (automatically set on "use proxies based on their predefined patterns). Result:

1) I can now navigate with Tor enabled on Firefox
2) if I check my IP at [http://whatismyip.com/](http://whatismyip.com/) I get two different IP addresses according to whether or not Tor is enabled 
3) if I check [https://torcheck.xenobite.eu](https://torcheck.xenobite.eu) I get the following message: 
[I]Your IP is NOT identified to be a Tor-EXIT.
So you are NOT using Tor to reach the web![/I]
4) if I check the "Tor Detector" (see [http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)) I get the following message: 
*Sorry. You are (probably) not using Tor.*

Any suggestion? Thanks again for your patience!

---

### Post by al.adab on 2008-04-11
Further update:

1) now [http://whatismyip.com/](http://whatismyip.com/) always detects the same IP address, regardless of whether or not Tor is enabled on Firefox
2) the IP address detected at [http://whatismyip.com/](http://whatismyip.com/) is the same [https://torcheck.xenobite.eu](https://torcheck.xenobite.eu) detects

---

### Post by hyperair on 2008-04-12
What did you do in between post #18 and #19? Tor was working fine in #18.

---

### Post by al.adab on 2008-04-12
Nothing was done between posts #18 and #19. I've just realised that both [https://torcheck.xenobite.eu/](https://torcheck.xenobite.eu/) and [http://whatismyip.com/](http://whatismyip.com/)  suggested that Tor is NOT actually working. If I uninstall FoxyProxy, and I try to navigate with Tor enabled, I can't open any website whatsoever. If I've re-install FoxyProxy...see post #18. It feels like denying reality at the moment: if I look at Firefox, I'm reassured that my IP is being hidden as I see the green "Tor enabled" icon. The moment I double-check that all this is for real...is anyone having the same problem? I can't believe it it's just me.

---

### Post by Sukarn on 2008-04-12
Try the FoxTor addon for firefox. When you enable using Tor in firefox through that addon, it checks whether the ip change was successful or not.

I've used this plugin to debug tor on my system in the past.

---

### Post by al.adab on 2008-04-12
FoxyTor installed. It confirms "Putting on your Mask...Done" if I navigate on "Tor enabled" + "FoxyProxy Default (for all URLs)". If it can be confirmed that at this stage I shouldn't worry about any of the messages I get when I connect to Xenobite or [http://whatismyip.com](http://whatismyip.com), that is, I'm safely navigating on the assumption that (otherwise) FoxyTor would give me messages like "your IP address hasn't been changed" (or the like), I can mark this thread as solved. 

If this assumption is wrong, can anyone please tell me what the ultimate test to verify I'm anonymously surfing the net is. 

Please bear in mind that without FoxyProxy I cannot open any website if Tor is enabled. 

Thanks.

---

### Post by hyperair on 2008-04-12
As long as your IP address before and after TOR is turned on is different, then you're fine.

---

### Post by Sukarn on 2008-04-12
> **hyperair said:**
> As long as your IP address before and after TOR is turned on is different, then you're fine.

And that test is exactly what is done by FoxTor.

[quote=al.adab]
FoxyTor installed. It confirms "Putting on your Mask...Done" if I navigate on "Tor enabled" + "FoxyProxy Default (for all URLs)". If it can be confirmed that at this stage I shouldn't worry about any of the messages I get when I connect to Xenobite or [http://whatismyip.com](http://whatismyip.com), that is, I'm safely navigating on the assumption that (otherwise) FoxyTor would give me messages like "your IP address hasn't been changed" (or the like), I can mark this thread as solved.
[/quote]
It indeed gives a message similar to "Failed to put on your mask. IP change failed" or something like that when your IP address with and without tor enabled are the same. Sorry, but I do not remember the exact message it gives. You'll know it when you see it though. Also, the icon changes to the mask icon, along with a red cross over the mask.

I like FoxTor because it offers added anonymity by not saving anything to the history, address bar, search bar and others while the mask is on.

---

### Post by dogbert04 on 2008-04-16
Ok folks, new user, same problem.... I need some more help here. I believe I have done the basics here and still have the problem that when tor is enabled I can't access any websites. I have the same setup as noted ealier in this thread, foxyproxy default to "use proxy default" for all urls, tor installed as it was on this thread, and foxtor.... foxtor cannot mask me at all, never has been able to. I have tried multiple tor and foxyproxy settings. I question whether this problem is truly solved. I am ready to try another solution altogether. Is there another proxy interface that works easier than tor in ubuntu gutsy???? Is there a linux alternative to gutsy that tor it setup easier than in gutsy?????

-LINUX NEWB.

---

### Post by A$h X on 2008-04-16
Grab Tor from the repo, then install foxyproxy from the mozilla firefox plugins page. Follow the install instructions on the Tor page and you should be good to go. Very easy to setup, not much editing of config files needed.

---

### Post by dogbert04 on 2008-04-16
ok, thanks, you have given me something else to try.

I went to spackagemanager first and completely removed tor and privoxy, then i followed the information here

[https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

except for changing it to gutsy, as I am....

I can say initially this fix has not worked even with sudo-restarting tor and p...

I won't reboot until the later am as I am busy with other stuff too.

thanks, hope this works, I have enjoyed tor in the enemy OS, and so far ubuntu except for what I don't 'get' yet.

anyhow, thanks again, and I enjoyed the 
"super cow powers" also...

-complete NEWB

---

### Post by A$h X on 2008-04-17
I followed the instructions on this page: 
[http://www.torproject.org/docs/tor-doc-unix.html.en](http://www.torproject.org/docs/tor-doc-unix.html.en)

(Ignoring step 2 and 3) and installed foxyproxy. It seems to work for me.

---

