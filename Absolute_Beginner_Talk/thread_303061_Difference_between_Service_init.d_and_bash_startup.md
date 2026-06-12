---
title: "Difference between Service init.d and bash startup"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by amirsarmad on 2006-11-19
hey all,

I just installed a fresh copy of ubuntu and wow! last time i used *nix was in 1999 with freebsd, this almost feels better than win.

Anyhow. IM running the following

PostgresSQL this has automatically started as a service (great)
Tomcat5.5 with appropriate java extensions.

now because i installed tomcat on my desktop /root/desktop. i cant really  load it  as a service( some mis configurations in the init.d/tomcat5.5 file or somthing). IM not a real linux guru so any help would be appreciated.

my questions are

a) whats the difference between running something through init.d as a service and through /etc/environment (bashrc.bashrc) which one is recommended.

b) why is running something as root bad. Because of security risks? 

c) is it possible to install PostgreSQL, Tomcat as differnet users?
for example tomcat as use tomcat and POSTGRESQL as user SQL. if so, how would i make my box startup with all these services running under a different user for example user "server".

d) whats the difference between ubuntu regular edition and server edition? would u guys recommend it for a server installation at a corporation, or should i user something like Redhat/Fedora/BSD..etc

thanx in advance

---

### Post by jaboua on 2006-11-19
a) init.d services can be made to run only at certain runlevels, and won't be started multiple times. It's easy to restart/stop/start them. I'm not sure what the enviroment-file does. If it's like a normal bashrc or bash_profile, it will either try to start your commands every time you log in, or every time you open a terminal...

b) Yes, security risks. Software has flaws - so if someone takes advantage of a bug in your services (for example if you run a mailclient as root, and someone sends you a mail that exploits a bug in your client), they can run whatever commands they want to as root... It's therefore safer to have as few processes as possible with root permissions. In addition it's the possibility of messing something up yourself...

c) Yes. I haven't done it myself and don't know the details, but my guess is that you have to change permissions of the binaries itself and perhaps the command that is used to launch them.

d) From what I've read before (I've never used the server version myself): Regular edition come with lots of desktop apps that are absent in the server edition. The server edition is basicly a stripped-down regular edition; it might also come with apache and stuff by default, I'm not sure about that. Anyway, if you want to you can always add missing applications that you want with "apt" or "aptitude", the software managment in ubuntu. I'm sure someone could help you out if you don't know how, just ask in the forums...

---

### Post by amirsarmad on 2006-11-19
BUMP BUMP.


can some one elaboretae questions C & D.

thanx in advance

---

### Post by stashj on 2006-11-21
I can only elaborate on D.

Server edition has no gui or any apps installed as default. It's as basic as they come and much better for running a server in production. As I see it, the less software there is on there the less security issues you may have and with no gui you get much better performance. If you want a web server you can do a LAMP install which will give you Linux, Apache, MySQL and PHP pre-configured but with apt-get making installing these so easy I don't even tend to go that far.

---

### Post by mike4ubuntu on 2007-01-03
not sure if this thread is still alive, but files like /etc/environment and /etc/profile are just global places for setting environment variables and command shell settings.  The kinds of things that you would put in your local .bashrc files but at a global level for all users.

Services (e.g. apache2, samba, networking ) are started through the /etc/init.d directory.  This directory goes hand in hand with the /etc/rc*.d directories.  You'll see a separate /etc/rc*.d directory for each of the run levels 0...6.  Run-levels 0,1, and 6 are for shutdown and 2,3,4,5 are for startup.  In those run-level directories you'll typically see symbolic links to scrips or programs in the /etc/init.d directory.  The scripts / programs in the /etc/init.d support the standard unixV conventions of start / stop / restart parameters.

Supposedly, in Edgy, there is a new event driven subsystem that provides a better way of handling services, but I can't find any documentation of it.  However, the /etc/init.d still works in Edgy.

---

