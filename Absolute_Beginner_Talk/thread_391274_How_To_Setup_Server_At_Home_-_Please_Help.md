---
title: "How To Setup Server At Home? - Please Help"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Bohica032 on 2007-03-23
Good Day.

I'm so new to Ubuntu, that i smell funny.  I have no previous experiance with Linux, so I need things explained to me like to a 5 year old.

I have an old PC, it use to have XP on it.  I want to convert it to a server, where I can connect to it through my home network, with possibility of connecting through the internet to retrieve some of the files, run PHP programs to store pictures, music, etc.

I am not command line kind of person.  I like the visual concept of operations, therefore I want the server to have the GUI interface, where i can do everything with the point and click.

Also I have 2 HDDs.  1st is a 20GB (master), where I want to set up Ubuntu, and 40GB as slave for extra storage.  I want the system to automatically use the 40GB as extra space as needed.

I will greatly appreciate any help i can get to get this machine up and running.  I have read some of the posts, here and read the linked tutorials and most of it to me is black magic.  I am a quick leaner, just need some things explained in detail or step by step.

PLEASE HELP!!!!!](*,) :?: ](*,)

---

### Post by devnulljp on 2007-03-23
You can ssh in using ssh -X and then launch all your graphical programs that way.
make sure /etc/ssh/sshd_config has this line

X11Forwarding yes

Then from your rmote commandline type ssh -X username@server
that will give you a console. make sure X is working by typing xclock, it should launch xclock on the remote server but display on your screen.

But I think you might be looking for something like vnc where you log on completely graphically.

---

### Post by Foudre on 2007-03-23
oh yes, installing a apache server is easy to work on a local network, but it won't have access to the out side world if you  are using a firewall router (most routers nowday do this by default, the normal ip address for this is : 192.168.0.1 , 
I'M SAYING THIS NOW CUASE IF YOU NEVER GET OUT SIDE, what good does it do, ok open like fire fox or what ever, insert that address into the url , hit enter, it should ask you for a log in, (consult your routers' manual for the log in, or if you had changed it, then your good)

you need to go to the section in the firewall option that allows for either exceptions or open ports, now pic a port number (port 80 is the default for web servers, but the router may be using port 80 so can't use it, I recomend port 8030 (just like it for some reason its an un used port by anything and easy number) ok allow this port, each router is different about this

after that is open, you'll want to change the configuration of the server to use this port. 

now to access it just use the local ip address for your computer while in your local network, out side your ip is different google find my ip, and you can find it quickly, use this ip as a url to access your web server with  :8030 at the end example
127.0.0.1:8030/videos or what ever, there are guides out there for setting up 

apache, and its availible via aptitude just go add remove programmes look for apache, or go to a command prompt and type sudo apt-get install apache (apache is a good free server software, most widely used)

---

