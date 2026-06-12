---
title: "Problems with Amarok and internet"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by DarthSudaka on 2006-09-28
Hi!
I'm using Ubuntu 6.06, gnome and k7 kernel.

I installed Amarok and works fine, but it doesn't seem to be able to retrieve any information from the internet.
Wikipedia Search on the artist tab says it can't connect to the server, and LYRC lyrics script doesn't work either. Says ERROR CODE 1.
It doesn't download album covers from Amazon either.

I have to use a proxy to connect to the internet but it is properly configured in System / Preferences / Proxy.

What can be happening?? :confused: 

Thank youuu!!!

Belowed I pasted the complete error log from LYRC, in case it is helpful:
/usr/lib/ruby/1.8/net/http.rb:562:in `initialize': Connection refused - connect(2) (Errno::ECONNREFUSED)
	from /usr/lib/ruby/1.8/net/http.rb:562:in `connect'
	from /usr/lib/ruby/1.8/timeout.rb:48:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
	from /usr/lib/ruby/1.8/net/http.rb:562:in `connect'
	from /usr/lib/ruby/1.8/net/http.rb:555:in `do_start'
	from /usr/lib/ruby/1.8/net/http.rb:544:in `start'
	from /usr/lib/ruby/1.8/net/http.rb:1031:in `request'
	from /usr/lib/ruby/1.8/net/http.rb:771:in `get'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:122:in `fetchLyrics'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:187
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:172

---

### Post by PPAAUULL on 2006-09-28
Are you missing anything? I know that it is a KDE program and might need some Libs. You sure you have them all? Plus because it is a KDE program it might not be able to use some of the features that it has in KDE.

---

### Post by kkellner on 2006-09-28
hey,
I had the same problem.  to fix it I installed the KDE app kcontrol:

sudo apt-get install kcontrol

once it's installed launch it by typing kcontrol in the terminal and go to the network settings and set your proxy there also.  that should connect you through the proxy.

---

### Post by DarthSudaka on 2006-09-28
Thank you!!!!
Works great!!!!!!
I'm happy!! hehehe :-D 

Didn't work first time because I run
sudo kcontrol
and set the proxy there... guess that changed the proxy settings for the root user, right?

run it again just
kcontrol
set the proxy up et voilâ!! 

thank you!

---

