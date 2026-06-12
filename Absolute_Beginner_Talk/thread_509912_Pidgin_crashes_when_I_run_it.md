---
title: "Pidgin crashes when I run it"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-07-26
I just installed Pidgin (I tried both the .deb and the source) and both install just fine.  However, when I run pidgin, I get the following:

chris@desktop:~$ pidgin
Segmentation fault (core dumped)

Any idea what could be wrong?  Any help to get this program up and running would be greatly appreciated!

---

### Post by wolfen69 on 2007-07-26
do you want it for yahoo? or something else? if for yahoo- gyachi is the best chat client. it's in synaptic.

---

### Post by chrisf79 on 2007-07-26
I want it for AIM and Yahoo.  I love pidgin and have used it on Windows and would like to use it here too.

---

### Post by wolfen69 on 2007-07-26
did you try uninstalling and reinstalling? where did you get it from?

---

### Post by chrisf79 on 2007-07-26
I did purge it from this system and reinstalled.  I downloaded the .deb from the first google result when searching for "ubuntu pidgin" and I downloaded the source straight from [www.pidgin.im](www.pidgin.im)

Either way, I get the same exact error.

---

### Post by sgardne on 2007-07-26
Hello,

I have the exact same problem. Compiled and installed from source using included instructions. It starts then immediately crashes. This however does not happen if I run it in the console with sudo. If I run it that way, it runs fine, but I don't want to run it that way. Does anyone know what's going on?

Thanks,

-Scott

---

### Post by chrisf79 on 2007-07-27
Wow, you're right.  Sudo does make it start.  Weird bug I guess.

---

### Post by sgardne on 2007-07-29
Bump. Anybody know what we're doing wrong? I've tried uninstallnig and reinstallng. No dice.

---

### Post by sgardne on 2007-07-29
Here's the output of pidgin -d :

> (14:46:53) plugins: probing /usr/local/lib/pidgin/iconaway.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/spellchk.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/markerline.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/xmppconsole.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/convcolors.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/pidginrc.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/relnot.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/extplacement.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/ticker.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/gtkbuddynote.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/timestamp.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/timestamp_format.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/notify.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/history.so
(14:46:53) plugins: probing /usr/local/lib/pidgin/gestures.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libirc.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libmsn.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libaim.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libgg.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/buddynote.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libqq.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/joinpart.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/psychic.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/log_reader.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/offlinemsg.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libzephyr.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libicq.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/ssl-gnutls.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/liboscar.so
(14:46:53) plugins: /usr/local/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the P
URPLE_INIT_PLUGIN() macro?
(14:46:53) plugins: probing /usr/local/lib/purple-2/statenotify.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libxmpp.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libyahoo.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libjabber.so
(14:46:53) plugins: /usr/local/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the 
PURPLE_INIT_PLUGIN() macro?
(14:46:53) plugins: probing /usr/local/lib/purple-2/autoaccept.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/idle.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/ssl-nss.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libnovell.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/libsimple.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/ssl.so
(14:46:53) plugins: probing /usr/local/lib/purple-2/newline.so
(14:46:53) util: Reading file accounts.xml from directory /home/scott/.purple
(14:46:53) util: Error parsing file /home/scott/.purple/accounts.xml.  Renaming old file to accounts.xml~
(14:46:53) util: Writing file accounts.xml~ to directory /home/scott/.purple
(14:46:53) util: Reading file status.xml from directory /home/scott/.purple
(14:46:53) stun: using server 
(14:46:53) stun: using server 
(14:46:53) gtkblist: added visibility manager: 1
(14:46:53) docklet: created
(14:46:53) util: Reading file blist.xml from directory /home/scott/.purple
(14:46:53) prefs: Reading /home/scott/.purple/prefs.xml
(14:46:53) prefs: Finished reading /home/scott/.purple/prefs.xml
(14:46:53) prefs: removing pref /purple/debug/timestamps
(14:46:53) plugins: Unable to find saved plugin /usr/lib/gaim/docklet.so
(14:46:53) plugins: Loading saved plugin /usr/local/lib/pidgin/notify.so
(14:46:53) pounce: Error reading pounces: Failed to open file '/home/scott/.purple/pounces.xml': No such file or directory
(14:46:53) Session Management: ICE initialized.
(14:46:53) Session Management: Connecting with no previous ID
(14:46:53) Session Management: Handling new ICE connection... (14:46:53) done.
(14:46:53) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000118573841300000056870017
(14:46:53) Session Management: Using pidgin as command
(14:46:53) Gtk: Theme directory 16x16/filesystems of theme nuoveXT.2.1 has no size field

(14:46:53) Gtk: Theme directory 22x22/filesystems of theme nuoveXT.2.1 has no size field

(14:46:53) Gtk: Theme directory 24x24/filesystems of theme nuoveXT.2.1 has no size field

(14:46:53) Gtk: Theme directory 32x32/filesystems of theme nuoveXT.2.1 has no size field

(14:46:53) Gtk: Theme directory 48x48/filesystems of theme nuoveXT.2.1 has no size field

(14:46:53) Gtk: Theme directory 64x64/filesystems of theme nuoveXT.2.1 has no size field

(14:46:53) Gtk: Theme directory 72x72/filesystems of theme nuoveXT.2.1 has no size field

(14:46:53) Gtk: Theme directory 96x96/filesystems of theme nuoveXT.2.1 has no size field

(14:46:53) util: requested to fetch ([http://192.168.1.1:5431/dyndev/uuid:000f-660c-866d0000cbdc](http://192.168.1.1:5431/dyndev/uuid:000f-660c-866d0000cbdc)), full=1, user_agent=((null)), http11=1
(14:46:53) dns: DNS query for '192.168.1.1' queued
(14:46:53) Session Management: Received first save_yourself
(14:46:53) dns: Created new DNS child 6759, there are now 1 children.
(14:46:53) dns: Successfully sent DNS request to child 6759
(14:46:53) Session Management: Received save_complete
(14:46:53) docklet: embedded
(14:46:53) dns: Got response for '192.168.1.1'
(14:46:53) dnsquery: IP resolved for 192.168.1.1
(14:46:53) proxy: Attempting connection to 192.168.1.1
(14:46:53) proxy: Connecting to 192.168.1.1:5431 with no proxy
(14:46:53) proxy: Connection in progress
(14:46:53) proxy: Connected to 192.168.1.1:5431.
(14:46:53) util: Request: 'GET /dyndev/uuid:000f-660c-866d0000cbdc HTTP/1.1
Connection: close
Host: 192.168.1.1:5431

'
(14:46:53) util: Response headers: 'HTTP/1.0 200 OK
SERVER: LINUX/2.4 UPnP/1.0 BRCM400/1.0
DATE: Sun, 29 Jul 2007 14:45:53 GMT
CONTENT-TYPE: application/octet-stream
Cache-Control: max-age=1
PRAGMA: no-cache
Connection: Close

'


---

### Post by Barny on 2007-10-27
Hi,

I have th same issue with pidgin and gaim. I can run it with root privileges, by using sudo, but not with normal privileges. I'm getting the same eror messages as sgardne, when running

```

pidgin --debug

```

This is since an upgrade on Gutsy Gibbon last week.

Did you find a solution to run pidgin or gaim without sudo?

Thanks
Barny

---

Please ignore this post. I was able to resolve it. After starting pidgin with sudo I created my accounts. and ended pidgin. After the accounts have been created, pidgin works with normal user rights, too.

---

### Post by MegaJim on 2007-10-27
which version of pidgin is this?

---

### Post by ftmichael on 2007-12-17
I had the same issue with 2.3.0 in Gusty; I got the .deb file from getdeb and installed it that way.  Adding the accounts didn't fix it.  I tried uninstalling pidgin, pidgin-data, and libpurple0 again, deleting the .purple directory entirely, and then reinstalling pidgin-data, lippurple0, and then pidgin.  It started and ran fine after that.

... until it crashed again.  Trying to restart it gave me the same error I'd been having in the first place.

I finally fixed it by following the instructions at [http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177](http://www.linuxmint.com/forum/viewtopic.php?f=47&t=7177) , which enabled me to install 2.3.1 from a third-party repository.  No problems at all with 2.3.1.

Michael

---

### Post by theShaggy on 2007-12-22
Running Pidgin was fine up until I tried to install Xfce as a second Desktop Manager... since you aren't able to decide what you want to install at the time, it threw in pidgin 2.2.0 and refused to run.

Instead, I uninstalled Xfce and came back to Gnome.  However, since then it doesn't like being shut down and opened up again.  Every time I do so it just closes immediately.  Running it through terminal gives me **pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error** as an error, and I have to delete my accounts.xml and re-add them all.

I've reinstalled, I've .configured.  I haven't deleted my whole purple directory... maybe that would help.

Anybody else have ideas of what is going on?

---

### Post by start2046 on 2008-05-19
I got the same problem,and sudo was fine.

But I notice pidgin has crashed after I opened the debug window in Help and enabled a new [COLOR="Red"]XMPP[/COLOR] account.From then,each time I run the program,it crashs.

I disable all the accounts in .purple/accounts.xml,and run it again.It's fine.

Hope this is helpful for you.

---

