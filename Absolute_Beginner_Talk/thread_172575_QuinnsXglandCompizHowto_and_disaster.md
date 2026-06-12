---
title: "QuinnsXglandCompizHowto and disaster"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-08
I just followed Quinns Xgl and Compiz Howto in the wiki and it didn't work. I finished going through the howto and did ```
sudo /etc/init.d/gdm restart
``` as it said. Now I see a black screen with white text. I have access to the terminal only. :confused: :( ](*,)  Can I still salvage setting up my compiz? Thanks!

---

### Post by Belathor on 2006-05-08
I'm back in X. Thanks to the usefulness of the #ubuntu support group!

> Belathor>	Hi, I have just followed the Howto in the wiki to enable XGL and Compiz and now I have no GUI at all. However, I have command line and have been trying to see if I messed up typing anything in the'/etc/X11/xorg.conf' . I am doing this is in nano because gedit doesn't work. I'm a newbie and am at a loss to figure out how I'm supposed to exit nano back to the command line. I see it says ^X but when I type it and press enter nothing happens. So, how can I get back to the command line? And once there, how can I get GUI back? And how can I get XGL and compiz working? Thanks for your help!
	<eggzeck>	Belathor, 'write-out' means exit
	<slackern>	Belathor: to close and save in nano press control+x
	<eggzeck>	Belathor, so ctrl+o
	<eggzeck>	I mean yeah ctrl+x hahahahaha nano sucks anyways
	<K-rad>	how do i find out what device file irda is?
	<Belathor>	lol
	<slackern>	control+o is to write the file without exiting.
	<eggzeck>	slackern, yeah I got mixed up :), I use vim anywho hehe
	<Belathor>	thanks for that!
		<intelikey>	Belathor one of those questions i can answer. there is by default about 6 login tty's (consoles) waiting to be used, the hot keys [alt]+[ctrl]+[F#] where # is 1-6 takes you to them. X normally lives in tty7 [alt]+[ctrl]+[F7] linux is fun that way.
	<nickrud>	linuxcn, [https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)
	<intelikey>	linuxcn install the build-essential package and the linux source then configure and make your kernel
	<Belathor>	cool
	<linuxcn>	thinks
	* intelikey	tries not to think
	* nickrud	admires thinkers
	* penguin-1	has to think about that
	<nickrud>	intelikey, :)
	<penguin-1>	;)
	<intelikey>	:)
	<intelikey>	really i've really tried hard to not think. but every time i'm almost there i loose my concentration and..... well you know the rest.
	<Belathor>	so yeah, I just pressed alt + ctrl + F7 and sure enough, all I get is a blinking line
	<hollowlife1987>	type 'startx'
	<Belathor>	who? me?
	<hollowlife1987>	yes sorrry
	<intelikey>	Belathor that's not good. is X supposed to be running?
	<Belathor>	well, startx did the trick
	<Belathor>	I have x again
	<Belathor>	wow
	<intelikey>	i have seen a really messed up X that couldn't handel switiching ttys... glad that wasn't your case.
	<Belathor>	me too (-=
	<Belathor>	hollowlife1987, thanks!
	<hollowlife1987>	Belathor, your welcome :)

So yes, all I had to do was type startx. LOL

---

### Post by Belathor on 2006-05-08
How can I tell if I'm using XGL?

---

