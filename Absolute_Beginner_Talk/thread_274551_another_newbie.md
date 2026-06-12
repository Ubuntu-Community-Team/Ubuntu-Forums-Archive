---
title: "another newbie"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Yorky on 2006-10-10
G'Day eveyone,

I am trying to setup my home network. I have 3 windows (XP & 2000)machines and 3 Ubuntu machines:
2 XP desktops 1 being the wifes, 1 being mine,
2000 is on 1 laptop which also has a split hardrive with Ubuntu,
1 Ubuntu desktop,
1 Ubuntu server.
I would like to setup the server with Samba so that the windows machines can store and access files on it.
I previously attempted this with Fedora Core 4 which had a graphical view of the server, this time my Ubuntu server seems to be all command line which is slowing my progress because my command line experience is very limited.
My Ubuntu desktop can see my windows machines because I was able to change it to WORKGROUP.
My Ubuntu server currently sits there with a scary looking 
ubuntuserver$ prompting me to type something
I understand I need to access the /smb/conf file and make some changes but Ive never used nano as an editor.
To cut a detailed question down a little.
Can I access a graghical view or some easy to follow instructions to configure via command line of my server.
My server has 2 hardrives 1 for the Ubuntu setup and one which is for all the files.


Yorky

---

### Post by TheWizzard on 2006-10-10
i think ubuntu-server is more for professional servers. if you just need a file-server for your home network, you can just  use a normal ubuntu. 

i don't know if x is available in ubuntu-server. try: startx. 

if x is not available, i would advice you to use the normal ubuntu and, once you got it working, shutdown x to save resources. 

if you had smb working in fedora, configuration is very easy: just use your backup of the /etc folder from fedora to replace the smb files.

---

### Post by PriceChild on 2006-10-10
There is absolutely no reason why you shouldn't do a full install on the server.

All the server install is, is a desktop install without any packages for graphical apps or the DE installed.

You can simply set up your server graphically, then do a 
[code]sudo /etc/init.d/gdm stop[/stop]to stop the gdm if you really want to conserve resources.

Pricey

BTW.. in the future could you please rename your threads with something meaningful? You will get MUCH MUCH MUCH better help as people with experience with "filestores" for example will be more inclined to take a look to see if they can help. It also helps the search feature :)

---

### Post by Yorky on 2006-10-10
thanks for the advice, both on the server and advice on naming my threads.

Cheers

---

### Post by petri on 2006-10-10
There is a couple of howtos to ubuntu servers, first one to ubuntu server at [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) and second one to a LAMP server at [http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06) there you find about webmin which may be easier to administration of server. I haven't used these howtos yet but I hope I'll do it soon :)

---

