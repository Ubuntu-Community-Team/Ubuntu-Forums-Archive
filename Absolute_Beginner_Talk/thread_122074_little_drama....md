---
title: "little drama..."
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by cmongini on 2006-01-26
hi 
i´m a newbie in linux and ubuntu, and by trying to costumize my control panel i deleted it completely! so i don´t have anymore access to any tools! 
please could somebody tell me how to:
1) access the terminal without panel
2) the linux commands to create a new account (that hopefully will come with a nbew conmtrol panel!)
thanks a lot!!!
claudia

---

### Post by dueY on 2006-01-26
Quick fix is you could create a launcher for "gnome-terminal" :p

---

### Post by cmongini on 2006-01-26
wherev is the gnome terminal? i don´t have a find function anymore....

---

### Post by Perfect Storm on 2006-01-26
<alt>+<F2>
gnome-panel

---

### Post by cmongini on 2006-01-26
thanks. this makes already a lot possible again. but i can´t find the way hhow to get the root commands from there...
could you please tell me the linux commands to make a new account from the terminal...
thanks again

---

### Post by az on 2006-01-26
sudo adduser user

---

### Post by cmongini on 2006-01-26
thanks i just tried this. but when i try to lo in with the new profile  it says that there is no  home folder for the new user, and 10 secs later comes back to the login window saying that the system is unstable...any hints to solve this problem? 
thanks

---

### Post by kaamos on 2006-01-26
Are trying to create a new user just because you messed up your gnome config? It would be easier just to rename the .gnome .gnome2 and .gnome2_private directories in your home folder (hidden, press control+h) and log out and back in.

---

### Post by cmongini on 2006-01-26
just tried it but the tool bar won´t come up again ( all the symbols in the upper right corner are away!)

---

### Post by kaamos on 2006-01-26
You must add them manually, just right click on the panel and use the "add to panel"

---

### Post by cmongini on 2006-01-26
the problem is i don´t have a panel anymore!!!

---

### Post by kaamos on 2006-01-26
Sorry, you said you were missing the symbols in the upper right corner so I thought you had gotten the panel back. Anyway, what is wrong with what Artificial Intelligence suggested? If sudo (root apps like synaptic) is not working for you, it probably has nothing to do with the panel.

---

### Post by cmongini on 2006-01-26
alt+ f2 is working! that is already one step! as now my settings are quite empty, a new account is not such a hassle..so i could have again  the full features...
the root commands do work it is just that i can´ t access them (for example the network configuration) i´m looking at the add user command  and tried to define the dir in this way:

root@skino:~# adduser --home DIR newacc
the answer was:
adduser: The home dir must be an absolute path.
have u an idea what it means? 
thanks again!

---

### Post by towsonu2003 on 2006-01-26
if I understand correctly, ou are missing the panel that's supposed to be on the top of your screen? the one with "Applications", "Places", "System" menus and the sound and date thingies (top right corner)? If tha's so, try this one: 

1. right click the panel that's on the buttom of your screen (pleeeeeaaaase don't tell me you don't have the bottom panel too ;) ), which shows which programs are up and running like firefox and whatever you run on your current workspace  and click "new panel"
2. move the new panel to the top of your desktop so it's sitting there horizontally
3. if the panel is too wide per your liking, right click and downsize it using "properties">"size"
4. right click your new panel and click "add to panel"
5. add "menu bar" which is "Applications""places""system"
6. If it's in the wrong place, right click on the new addition, click on "move" and move it to where you want it to be"
7. goto 4 and add "notification area"
8. move the ||||||||| like looking thing whereever you want (towards right, leaving additional space for below)
9. right click on the new notification area (right of the ||||||||| like looking thing) and add "clock", move it where you want
10. right click on the new notification area and add "volume control"
11. right click on notification area and add "battery charge monitor" (for laptops)
12. now move everything to your liking and when you are sure they are in their correct places in the panel, right click to each one and choose "lock to panel"
13. take a look at what else you can add to the panel (for fun) ;)

Hopefully, this will solve the problem without a new account and so on. 

while you are shutting the pc down, choose "save this session" on the logout screen, just in case ;)

PS. if you still need a new user, "man adduser" might help. a new user needs a new home directory, so create a new dir for him/her (sudo mkdir /home/newusername) and specify the path while using adduser. also, if you get permission errors while logging in w/ new user account, change the ownership of /home/newusername with ```
sudo chown -R newusername:newusername /home/newusername
``` while being carefull with that chown command.

PS. if the above 13 steps worked for you, synaptic etc. should work flawless. if you click system>administration>synaptic and it doesn't launch or doesn't accept the password, that's another problem. in that case, use ```
sudo synaptic
``` in a terminal (alt+f2 -> gnome-terminal) and copy/paste output here.

---

### Post by cmongini on 2006-01-27
thanks a lot!!!this has done it!!

---

### Post by towsonu2003 on 2006-01-27
> **cmongini]thanks a lot!!!this has done it!![/QUOTE]
I'm glad (i'm also glad you had the panel that's at the bottom of the desktop  said:**
> 13. take a look at what else you can add to the panel (for fun)
did you find anything fun? ;)

---

### Post by cmongini on 2006-01-27
well actually i had a rapid look thru but as i´m still dealing with other problem i didn´t spend that  much time....may be you have an other good hint: 
i have the linux computer connected to the internet ( lan) via eth0. This computer has an other card, eth1, that connects to a windows laptop. both cards are configured, the two computers ping each other but the laptop can´t access the internet! i´ve been told that i have to 
a) set up the ip forwarding
b) setting the IP tables.... 
can´t find any way to do it.........
thanks for any suggestion!

---

### Post by towsonu2003 on 2006-01-27
[QUOTE=cmongini]
a) set up the ip forwarding
b) setting the IP tables.... 
[/QUOTE]
although I'm mostly clueless about that stuff, you could try firestarter (a firewall, apt-gettable, very simple to use, will be up once set up using wizard). you could set up your ip tables using its wizard. I remember that it has options for network sharing etc. not sure if it would help, but may be worth trying.

PS. just a note: a gui firewall in linux is just an easy frontend to configuring iptables.

---

### Post by cmongini on 2006-01-27
feeling a bit stupid...but i installed the program (and others) and i can´t find the executables..( they are not in the applications menu) where could i find them? 
thanks again

---

### Post by Jason_25 on 2006-01-27
For NAT/MASQ, read this:
[http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

Now read my post #3 here:
[http://www.ubuntuforums.org/showthread.php?t=60501](http://www.ubuntuforums.org/showthread.php?t=60501)

Once done you should be able to share your connection with other computers.
Any questions just ask.

edit: btw, if you are connecting the laptop and pc directly together without a hub, you will need a crossover cable.

---

### Post by towsonu2003 on 2006-01-27
[QUOTE=cmongini]feeling a bit stupid...but i installed the program (and others) and i can´t find the executables..( they are not in the applications menu) where could i find them? 
thanks again[/QUOTE]
no need to feel that way. firestarter should go under applications>system tools>firestarter
if it's not there, do ```
killall gnome-panel
``` and it should appear. if it doesn't, open up a terminal (alt+f2 -> gnome-terminal) and type ```
gksudo firestarter
``` firestarter needs root privileges (your password) to configure the iptables. 
usually, all applications will launch from a terminal when you call their names (firestarter, dillo, epiphany, lynx etc). if killall gnome-panel (which refreshes gonme-panel by killing and re-launching it) doesn't work, you can add the applications to the menu using applications>system tools>applications menu editor. 
most applications you get using apt-get (synaptic) will show up in the menu. applications you compile by yourself (if you need to type ./configure make make install or make checkinstall in a terminal, that means you are compiling an application) will not.

---

### Post by cmongini on 2006-01-27
thanks to both for the hints! good to know that i can start any program by tiping the name in...
i tried both the possibilities for the networking and put in the terminal the ip forwarding comand. the problem is that gedit won´ t let me save the file in the folder 
you suggested (i´ m afraid of changing the permission of the folde, as today i had already to reinstall the system completely because i changed the permissions of the usr folder to 777 and because of this there was no way to call up the root again) 
is there a sure way to change permissions?

---

### Post by towsonu2003 on 2006-01-28
[QUOTE=cmongini]the problem is that gedit won´ t let me save the file in the folder 
you suggested [/QUOTE]
could you quote that suggestion? I can't find it here? I'm lost ;) thanks :)
to quote: [ q u o t e = nickname ] blablabla [ / q u o t e ] without spaces.

---

### Post by cmongini on 2006-01-28
thanks for still following my page...

the quote: 
[QUOTE = Jason_25] For NAT/MASQ, read this:
[http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/](http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/)

Now read my post #3 here:
[http://www.ubuntuforums.org/showthread.php?t=60501](http://www.ubuntuforums.org/showthread.php?t=60501)

in the link: 
Have you seen this page? Check out section 3.4. You'll want to paste that stuff into gedit and create a file called rc.firewall-iptables and save it to /etc/init.d/. You'll need to edit to your needs. Then you should do a chroot 700 on it to make it executable. Finally, do a update-rc.d on the same file and it should run when you reboot. I'm sure there's a better way to do it than that though.[/QUOTE]

 unfortunately i still have the problem of not beeing able to launch all the programs...it went fine for firestarter ( although then it didn´t do the purpose or i couldn´t make it!) but all the rpograms i´ve installed using synaptic still don´t appear in the applications menu (tried your suggestion). for ex i installed dvd author, or dvd+rw-tools and i can´t launch these programs by writig the command. where could i find the application ? (maybe i could make a link to it!) 
moreover i found some software on softpedia that is not listed in the repositories...i had downloaded it but then no idea how to install it....

thanks a lot![HTML][/HTML]

---

### Post by towsonu2003 on 2006-01-28
[QUOTE=cmongini]the problem is that gedit won´ t let me save the file in the folder 
you suggested[/QUOTE]
important: don't change the permissions of any folder/file outside /home/yourusername (your home directory, also known as ~/ ). 
type ```
sudo -s -H
``` which will give you root privileges until you type ```
exit
``` and follow the instructions (which, I have no idea whether they work in ubuntu).

be very very very careful about what you are doing after typing sudo -s -H
any misspelling or mistyping may break your installation. I saw people mistyping and deleting each and every data in their hard disk. before hitting enter, check your command 3-4 times (that's what I do). 

type ```
exit
``` when you are done with the howto. don't launch any application bf typing exit, as the application will launch with root privileges (dangerous, very insecure). 

PS1. did you search the forum for an easier method? not sure if this is easier but: [http://ubuntuforums.org/showthread.php?t=91370&highlight=share+network](http://ubuntuforums.org/showthread.php?t=91370&highlight=share+network) ?

PS2. In firestarter, there is an option for internet sharing while running the wizard. just a note. 

> for ex i installed dvd author, or dvd+rw-tools and i can´t launch these programs by writig the command. where could i find the application ? (maybe i could make a link to it!)
have no idea as I never used them. if no one answers to that here in a day or two (which is likely bc of the number of posts here), u may wanna post a new thread to Absolute Beginners, after searching the forum of course ;)

PS3. when quoting, don't use any spaces between the characters in the brackets ([]) Quoting is fun ;)

---

### Post by cmongini on 2006-01-28
[QUOTE=towsonu2003]PS1. did you search the forum for an easier method? not sure if this is easier but: [http://ubuntuforums.org/showthread.php?t=91370&highlight=share+network](http://ubuntuforums.org/showthread.php?t=91370&highlight=share+network) ?[/QUOTE]
thanks a lot this worked...slowly i´m getting into the ubuntu dimension...
i really appreciated your very clear responses that avoided me lot of frustration;)

---

### Post by Trix on 2006-01-28
[QUOTE=towsonu2003] 
13. take a look at what else you can add to the panel (for fun) ;)
[/QUOTE]

:shock:

THANK YOU.  I switched to Ubuntu a few weeks ago, and I never knew I could add to the panel that way. The one thing I missed from XP was having the temperature in the taskbar, and I spent hours trying to configure gdesklets to at least have it on my desktop. Now it's back in my panel where I really wanted it.  I know it's a minor point, but I thought I'd let you know someone else benefited from your help in this post. :)

---

### Post by towsonu2003 on 2006-01-28
hey, I'm glad the suggestions worked! especially the network one bc I wasn't sure I was gonna be able to help (w/ my ignorance on how networks work).

---

