---
title: "::no-ip problem::"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by grim918 on 2006-05-09
I am trying to install no-ip but i am having some problems. 
To install the no-ip client i used:
```
sudo apt-get install no-ip
```
everything goes ok. i also created an account with no ip and everything seems to go ok with that.

Then i go to canyouseeme.org. i check to see if the port is open and it says that it can see me and that my isp is not blocking the port. I have apache running on the comp on port 80 but I cant view it with the browser on another computer. It tells me that the connection is refused. Does anyone know how to fix this, and point out what I am doing wrong.

---

### Post by kspr on 2006-05-09
It seems to me that your you.no-ip.com adress does not redirect to your ip. So maybe your no-ip updater program is not configured correctly. 

Have you tried: 

Connecting to your webserver from another computer using your own ip-adress directly? If you type 
$ ifconfig 
you will see "inet addr: xxx.xxx.xxx.xxx" on eth0 or whatever you are using.

If that works, login to no-ip.com's website and manually check that your you.no-ip.com redirects to the correct ip. If it's the incorrect ip then you do have some problem with the automatic updater program.

you can also check this by typing: 
$ host your.no-ip.com

if it resolves to your ipadress it's working like a charm.

Another thing is that it can take a while (usually a couple of minutes) before you submit an update of ip to the no-ip forwarding database, and the redirecting works.

---

### Post by grim918 on 2006-05-09
I have tried to connect to the computer with another computer but it says that the connection is refused when i try to connect with ssh. If i try to view the webserver on port 80 with a browser i get a page not found. I dont know what the problem could be. With no-ip, when you enter the ip address do are you supposed to enter the internal ip address or the external ip address. thank you for any help

---

### Post by linuxusr50 on 2006-05-09
I am not exactly sure how much hou have been able to test, so I will give you some things to try.

```
ps -A | grep -i ssh
```
make sure you have sshd running.

```
ps -A | grep -i apache
```
see if you have apache2 running

go to your browser and type in the IP of the machine running your apache web server and  see if you are able to get your web page.

If all of these succeed, make sure you have allowed ports 80 and 22 to forward to the machine that is running these services.

If you are still having problems try to run and replace the X's with your IP.  You may have to install nmap if it is not installed already.

```
nmap X.X.X.X
```

NMAP should show ports 22 and 80 being open if you have the services properly configured.

Your problem really sounds like you may not have your router set up correctly or you have a firewall blocking port 80 or 22.

Luck

---

### Post by grim918 on 2006-05-11
I have checked everything and everything is working as it should. When I check if my webpage is working it will only show if I type in the internal ip address or localhost. It will not work if I type in the external ip address. When I go to canyouseeme.org it says that it can see my service and that the isp is not blocking the port. This leads me to believe that everything is working correctly. I have verizon dsl. Does anyone know if verizon has something set up where you cant set up port forwarding. I have done everthing else. I forwarded the ports on my router, I configured my firewall, I checked to make sure that all the services are running, and everything works great locally. When I try to use another comp to connect that is not local nothing works. I am lost with this one.

---

### Post by grim918 on 2006-05-11
nevermind I got it working now. I guess it just took a while for the changes to update or something. I didnt change anything and now it just works. thanks for the help.

---

### Post by grim918 on 2006-05-18
I installed and configured no-ip to work on Ubuntu and everything is going well. I am now having a problem with my internet connection. I have DSL and it keeps connecting and disconnecting. This causes a problem when I am remotely logged into my computer because I cant get any work done. The internet connection problem started after I installed no-ip. I dont know what could be causing this problem. I was wondering if anyone has had any kind of internet connection problems after installing no-ip. Maybe I screwed something up, or maybe its just Verizon thats having the trouble. Either way I would appreciate any help. Thank you.

---

### Post by sailor2001 on 2006-05-18
connecting and disconnecting sounds like a clock problem      sudo ping -t [http://www.(any](http://www.(any) url)  I use 10 as a time value

---

### Post by grim918 on 2006-05-18
how do i fix the clock ping thing. I dont understand.

---

