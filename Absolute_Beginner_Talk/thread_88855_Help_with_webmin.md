---
title: "Help with webmin"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by Brad.G on 2005-11-11
Ok im new to linux, but learning lol.

i have root access to our server at work , and im trying to set up a new user group on the server. the bit i cant figure out is how to configure where they are allowed to go?.

it will be a very limited group , basically access to one folder on the server.

how do i go about this anyone?

---

### Post by Brad.G on 2005-11-11
from what ive figured out so far.. i have to create a folder in the home directory of the server, then edit the folders properties and assign it to a group?

thing is it says im not the owner so it wont allow me to create a new folder here. im logged on in the same account the IT tech uses .. 

tried logging in as 
root
password

but says administrator cannot log in from this screen.

---

### Post by apjone on 2005-11-11
[QUOTE=Brad.G]from what ive figured out so far.. i have to create a folder in the home directory of the server, then edit the folders properties and assign it to a group?

thing is it says im not the owner so it wont allow me to create a new folder here. im logged on in the same account the IT tech uses .. 

tried logging in as 
root
password

but says administrator cannot log in from this screen.[/QUOTE]
If you are trying to log in remotely the IT guys may have disable remote root login ( I do it), this means you should login as yourself and then either 'su -' and enter the root password. If you are using ubuntu then login as yourself and either type 'sudo bash' or 'sudo *command* . Best if you contact your IT guys thou.
#su -
password: ********

---

### Post by Brad.G on 2005-11-11
lol thats the thing i am the IT guy  :???: 

the IT tech retired a couple of weeks ago. he managed the server remotely ( and very well ) and i maintained all of the win32 OS's on the network. so now im on a steep learning curve with linux.

i have direct access to the server, i have all the usernames and passwords. just tryin to learn my way around ubuntu :) .

il try what you suggested above

---

### Post by apjone on 2005-11-11
[QUOTE=Brad.G]lol thats the thing i am the IT guy  :???: 

the IT tech retired a couple of weeks ago. he managed the server remotely ( and very well ) and i maintained all of the win32 OS's on the network. so now im on a steep learning curve with linux.

i have direct access to the server, i have all the usernames and passwords. just tryin to learn my way around ubuntu :) .

il try what you suggested above[/QUOTE]
Hey any joy? think bout it I think this might help

1) change root password to access webmin in ubuntu
sudo /usr/share/webmin/changepass.pl /etc/webmin root *password*

2) If the other Tech was security consious he may of tied down what IP's can access webmin goto [http://www.freeos.com/articles/2664/](http://www.freeos.com/articles/2664/)

look at this section

Webmin Configuration

On the page that is displayed click on the following icon.

Port and Addresses

The first option is the IP addresses on which Webmin will accept
connections. The whole point here is that, the local machine on which
Webmin is running may have several static and dynamic interfaces. You may
be connected to the Internet in more ways then one, and you surely don't
want Webmin to be accessible to everyone. That's the reason why you have
the option of specifying the interface on which Webmin should listen.

The next option allows you to mention the port on which the Webmin server
will accept requests. Change this from the default value of 10000, to any
other port in the range of 1025 - 65535. If possible, make sure no other
services are running on the port that you have chosen. One simple way of
cross checking is to look out for that port in the file /etc/services. If
you see any other service that requires that port and you are using it
already then choose another port.

---- IP Access Control ----

__ Allow from all addresses DDDDDDD
__ Only allow from listed addresses DDDDDDD
__ Deny from listed addresses DDDDDDD

Another important setting that I need to touch upon is the remote and
local addresses which can connect to the Webmin server. By default any IP
address can connect to the Webmin server. You should change this setting
to reflect the machine/machines from which you would allow connections to
the Webmin server. The drawback however is that you have to explicitly
mention every IP address that is allowed to make connections to this
server, the IP/Netmask pair doesn't work out here. This is not a problem
because you should allow access to Webmin from only a few trusted
machines. Every time you make a change to any Webmin configuration make it
a point to save the changes. Enabling logging and login timeouts is also
recommended.

AJ

---

### Post by Brad.G on 2005-11-11
Thanks for the post AJ

i can get in to webmin no problem

ht tps://localhost:10000

and log in with the root password

just when i go to

system files / home 

and try and right click to create a new folder it wont allow me. padlock on the pic on the left side.

tried logging out, putting root as the username, and then the password, but cmes up with " administrator cannot log in from this screen"  as ive learned that you cannot sign in as "root" ..

so how do i go about this?

just tried clicking system tools > shared folders > added a folder there, it didnt look right 

EG 

/root

not like the rest of them

/home

so i deleted it... now the prob there is that the other folders no longer show up in the entire network window on the win32 clients :o  good job theres shortcuts which go to them

\\server\ISM

for instance. the shortcuts work fine.

but anyway thats a problem il worry about later. for now i just need to figure out how to create a new folder in this home directory.

---

### Post by apjone on 2005-11-11
what linux are you running? and what exactly did you delete

---

