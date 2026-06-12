---
title: "tor on linux"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by tonab on 2007-02-09
hi all, i did a apt get for tor and privoxy they installd fine,tor buton is enabled in firefox and privoxy is blocking adds,my question is,  my ip is still showing on the test site, i need to make a comparison here so bear with me,when i used tor on windoze it came with vidalia the onion router ,what do i need to do to get the proxy chain working on my ubuntu 5.10.

---

### Post by shanepardue on 2007-02-10
make sure the tor and privoxy services have been started

```
sudo /etc/init.d/tor start
sudo /etc/init.d/privoxy start
```

---

### Post by Dr. Nick on 2007-02-13
you edit your privoxy config file per [http://tor.eff.org/docs/tor-doc-unix.html.en](http://tor.eff.org/docs/tor-doc-unix.html.en)

---

### Post by tonab on 2007-02-13
shanepardue  I have done that command they are working to a point

also the link Dr Nick sent is involved and a I will try to configure with it, part of the link mentions putting a command at the top of a config file and use the period . Im not sure where the top is and I dont want to mess it up, thanks

---

### Post by shanepardue on 2007-02-13
The part you are to add just goes at the very top of any text in the document. Push enter when you're at the top to give you a blank line then paste that entry on the top. That would do it!

---

### Post by Dr. Nick on 2007-02-13
yeah, all you really need form that link is to copy the one line anywhere in the file (they suggest the top). you will need to be sudo to edit it most likely.

Then run this from a terminal to restart privoxy, or just reboot your system

**sudo /etc/init.d/privoxy restart**

---

### Post by tonab on 2007-02-15
ok, it wont let me edit the config file, im not sure how to do this as sudo.

---

### Post by Dr. Nick on 2007-02-15
> **tonab said:**
> ok, it wont let me edit the config file, im not sure how to do this as sudo.

if you are in gnome and know where the config file is then type

[B]gksudo gedit /pathtofile
[/B] 

from a terminal and you should be able to edit it then, I think the site above mentions the default location for the config file

---

### Post by tonab on 2007-02-16
I got this message when typed gksudo command, (gedit:16252): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

it then opened a blank word document, the file path I used was /etc/privoxy and /etc/privoxy/config, both commands gave the same message,

---

### Post by Arisna on 2007-02-16
The Gnome-UI warnings are harmless and should not interfere with operation.  However, you do need to specify a particular file to edit, or open it from within the application.  Pointing it at a directory from command line probably will not work.

---

### Post by Dr Small on 2007-02-16
I have tor for my box, but I don't have Privoxxy. I couldn't get it to work.
So, I have tor button in Firefox, and the Preferences of Tor button are as follows:

_Proxy Settings_
* Use the Recommended Proxy settings for my version of Firefox

Privoxxy is unchecked.

And Use Custom Proxy Settings is not selected.

That gets tor to work for me ;)


Dr Small

---

### Post by Zyren on 2007-02-24
I am having a problem with Tor. It used to work, but now when i try to run using the command "sudo /etc/init.d/tor start" it gives me this:

 * Starting tor daemon (tor)... Feb 24 16:34:48.669 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Feb 24 16:34:48.670 [warn] config_assign_line(): Unknown option 'ReachableDirAddresses'.  Failing.
Feb 24 16:34:48.670 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.

i have no idea why its doing that considering it used to work. Anyone have any ideas?

---

### Post by PartisanEntity on 2007-03-01
Are the instructions mentioned in this thread going to have TOR running all the time, or can I choose when I want to be anonymous and when not?

In windows there was this nice tor button plug in for firefox to turn TOR on and off, does this exist for Ubuntu?

---

### Post by airtonix on 2007-03-01
there is a tor extension for firefox, "proxy switch" or similar name.

use it. it lets you switch between profiles of proxies. ie your isp dns or you privoxy dns.

---

### Post by Bluejacket on 2007-03-08
> **Zyren said:**
> I am having a problem with Tor. It used to work, but now when i try to run using the command "sudo /etc/init.d/tor start" it gives me this:

 * Starting tor daemon (tor)... Feb 24 16:34:48.669 [notice] Tor v0.1.0.16. This is experimental software. Do not rely on it for strong anonymity.
Feb 24 16:34:48.670 [warn] config_assign_line(): Unknown option 'ReachableDirAddresses'.  Failing.
Feb 24 16:34:48.670 [err] tor_init(): Reading config failed--see warnings above. For usage, try -h.

i have no idea why its doing that considering it used to work. Anyone have any ideas?

I have the same problem. It worked fine after I installed it, but tor doesn't start after a reboot. I get the same error message as you.

---

### Post by Bluejacket on 2007-03-30
> **Bluejacket said:**
> I have the same problem. It worked fine after I installed it, but tor doesn't start after a reboot. I get the same error message as you.

I got it fixed, in case someone has the same problem here's how to fix it:

The problem is that you are using old version of Tor, 0.1.0.16. Simply update tor, you can do it by adding repositories to your sources.list, instructions at [http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)

Restart Tor and it works. :popcorn:

---

### Post by DouglasCaixeta on 2007-10-26
Hi,

I have the same error above, and my tor version is 0.1.2.17.

```

Oct 26 10:06:19.696 [notice] **Tor v0.1.2.17**. This is experimental software. Do not rely on it for strong anonymity.
Oct 26 10:06:19.698 [notice] Initialized libevent version 1.3b using method epoll. Good.
Oct 26 10:06:19.698 [notice] Opening Socks listener on 127.0.0.1:9050
Oct 26 10:06:19.698 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Oct 26 10:06:19.699 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Oct 26 10:06:19.699 [err] Reading config failed--see warnings above.
```

The privoxy is running well:

```
Status of filtering proxy server: privoxy is running.
```

Any ideas?

---

### Post by Xezal on 2007-10-27
Dr. Small, thank you so much for your information on tweaking the Firefox preferences.  Your suggestion is what finally got the Tor working for me.

---

### Post by DouglasCaixeta on 2007-10-27
Hi,

So I passed the first step.

Now I receive another message, but TOR still not working.

```
Oct 27 21:02:18.887 [notice] Tor v0.1.2.17. This is experimental software. Do not rely on it for strong anonymity.
Oct 27 21:02:18.889 [notice] Initialized libevent version 1.3b using method epoll. Good.
Oct 27 21:02:18.889 [notice] Opening Socks listener on 127.0.0.1:9050
Oct 27 21:02:21.300 [notice] We now have enough directory information to build circuits.
Oct 27 21:02:32.463 [notice] Tor has successfully opened a circuit. Looks like client functionality is working.
```

Seems like working, but not. The pages identify my Ip address.

What can I do?

---

### Post by Nonc on 2007-11-01
was a solution to this found? i have the same problem as above.

cheers

---

### Post by DouglasCaixeta on 2007-11-01
Well, my tor is working now but I don't know why.
I configure the config of privoxy /etc/init.d/privoxy.

Put the code in last line:

```
127.0.0.1:9050 .


```

IMPORTANT: Need to have a space after 9050 and a point and an enter.
Exactly like that, or this will not work.

---

### Post by Nonc on 2007-11-01
either its not working or (more likly im doing it wrong). because it says it cant parse the config file now

should it look like this
```

N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
	exit 1
	;;
esac

exit 0 
127.0.0.1:9050 .


```
with that empty line at the bottom.

or something else?

---

### Post by DouglasCaixeta on 2007-11-01
Ok, Nonc, I'm sorry. The correct archive is:

sudo gedit /etc/privoxy/config

Not
/etc/init.d/privoxy

Sorry.

should it look like this

```

#close-button-minimizes 1

#  The "hide-console" option is specific to the MS-Win console version
#  of Privoxy.  If this option is used, Privoxy will disconnect from
#  and hide the command console.
#
#hide-console

#
forward-socks4a / 127.0.0.1:9050 .


```

Then, restart privoxy:

```
sudo /etc/init.d/privoxy force-reload
```

And Tor:

```
sudo killall tor

tor
```

---

### Post by Nonc on 2007-11-02
excellent, that and a few other things such as checking all the config files that it mentioned were there and had stuff in them has made it work.

cheers for your help

nonc.

---

