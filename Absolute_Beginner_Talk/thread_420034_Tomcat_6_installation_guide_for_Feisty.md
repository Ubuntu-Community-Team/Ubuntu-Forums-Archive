---
title: "Tomcat 6 installation guide for Feisty"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by garylai on 2007-04-23
[FONT="Arial"]I have tried the following steps, and it works smoothly on Feisty, hope this little contribution can help you setting your tomcat server.

_Step 1._ Download the latest Tomcat to your desktop: [http://www.apache.org/](http://www.apache.org/), then run
[B][I]sudo tar zxvf apache-tomcat-6.0.10.tar.gz
sudo cp -R apache-tomcat-6.0.10 /usr/share/tomcat6[/I][/B]

_Step 2. _Setting JAVA environment
Download the latest J2SE SDK, and run
[B][I]sudo chmod +x *.bin
sudo sh ./jdk*.bin[/I][/B]

Executing the .bin file creates a folder on your desktop named jdk1.6.0_01. Rename that folder to Java6u1. Now move that folder to /usr/lib
[B][I]sudo mv Java6u1 /usr/lib
sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java 300
sudo update-alternatives --config java[/I][/B]

1  /usr/lib/Java6u1/bin/java
2  /usr/bin/gij-wrapper-4.1
3  /usr/lib/jvm/java-gcj/jre/bin/java
Select 1
[U]
Step 3. [/U]Setting the following environment
 * /etc/environment*
***gedit /etc/environment***, then insert and save two lines:
[B]CLASSPATH=.:/usr/lib/Java6u1/bin
JAVA_HOME=/usr/lib/Java6u1[/B]
[U]
Step 4: [/U]Tomcat needs to set JAVA_HOME or JRE_HOME to execute. Open the follow document and edit the lines&#65306;
***sudo gedit ~/.bashrc***
then place the following lines in:
[B]export JAVA_HOME=/usr/lib/Java6u1
export PATH=$PATH:$JAVA_HOME/bin[/B]

_Step 5: _Start and stop tomcat
Now start your tomcat: ***sudo /usr/share/tomcat6/bin/./startup.sh* **
Type [http://localhost:8080](http://localhost:8080) in your browser. If you see the tomcat welcome page, your tomcat is running smoothly. If you are installing below 5.5 version, please try 8180.
Stopping tomcat: ***sudo /usr/share/tomcat6/bin/./shutdown.sh***

_Step 6: _Tomcat administrator setting
Edit this document:
***sudo gedit /usr/share/tomcat6/conf/tomcat-users.xml***
before **</tomcat-users>** insert this line:
**<user username="your username" password="your password" roles="admin,manager"/>**
Save and restart your tomcat. You can login to your tomcat admin by using your new set id and password now.[/FONT]

---

### Post by Sethiano on 2007-04-29
Thanks for a great HOWTO, it worked flawless :)

---

### Post by ahlandberg on 2007-06-16
Problem with Environment Variables:

Upon starting Tomcat with sudo /usr/share/tomcat6/bin/./startup.sh 

I get the following message:

ahlandberg@ubuntu610:/usr/lib$ sudo /usr/share/tomcat6/bin/./startup.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

I followed all the above instructions (except the Java setup, as I already had it installed).

My edited files look as follows:

#/etc/environment

CLASSPATH=.:/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_AU.UTF-8"


#~/.bashrc

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# Tomcat
[B]export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11
export PATH=$PATH:$JAVA_HOME/bin
[/B]

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi





--

I am new to Linux, and appreciate any help!

Thanks in advance!

Anders

---

### Post by ahlandberg on 2007-06-16
After I figured out that I reboot of the system would fix the above described problem, I now encounter the following problem.

I start tomcat with the following command:

[B]ahlandberg@ubuntu610:~$ sudo /usr/share/tomcat6/bin/./startup.sh
Using CATALINA_BASE:   /usr/share/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.11[/B]

However, when I load localhost:8080 in the web browser, it gives me a Problem Loading Page.

Question 1) How can I find out what the problem is? I have checked that the webapps directory is present.

Question 2) How can I find out whether the tomcat server is running with the ps -All command? I.e., which process should I look for?

Thanks in advance!

Anders

---

### Post by cuongnhc on 2007-06-30
> **ahlandberg said:**
> 
I start tomcat with the following command:

[B]ahlandberg@ubuntu610:~$ sudo /usr/share/tomcat6/bin/./startup.sh
Using CATALINA_BASE:   /usr/share/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME:       /usr/lib/jvm/java-1.5.0-sun-1.5.0.11[/B]
However, when I load localhost:8080 in the web browser, it gives me a Problem Loading Page.

Anders

have the same problem, anyone can help me plz... thanks

---

### Post by cuongnhc on 2007-06-30
oh i found it, had no apache2 installed :)

---

### Post by Depressed Man on 2007-07-08
It works! Thanks!

---

### Post by aliov_85 on 2007-07-09
Hello,

I tried to configure my tomcat with my old tomcat, and I haven't got any result, so I let fall,  I uninstalled and then I deleted all  java configurations.

Now I have some problems for installing properly java.
I got the newest jdk, I put it on my desktop, 

and after on the CLI I typed:

> sudo chmod +x jdk-6u2-linux-i586.bin
But when I tried this:
>  sudo sh ./jdk-6u2-linux-i586.bin[QUOTE]

I got this message:
[QUOTE]./jdk-6u2-linux-i586.bin: 1: Syntax error: redirection unexpected

Can anyone help me please?

---

### Post by lexarrow on 2007-07-17
Thaks a lot! Awesome howto. It worked perfectly!

---

### Post by gabo on 2007-07-18
> **cuongnhc said:**
> oh i found it, had no apache2 installed :)

I am new as well. How do I install apache 2. I have the same problem. Why do I need apachey 2, isn't only tomcat necessary? I only need to run some servlets.

---

### Post by gabo on 2007-07-18
I tried sudo apt-get install apache2 but it is still not working.  Then I tried to shutdown and...

Oh man! When I shutdown, this happens.

gabo@Turing:~$ sudo /usr/share/tomcat6/bin/./shutdown.sh
Using CATALINA_BASE:   /usr/share/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME:       /usr/lib/Java6u1
Exception in thread "main" java.lang.UnsupportedClassVersionError: org/apache/catalina/startup/Bootstrap (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
gabo@Turing:~$ 



Any suggestions?

---

### Post by gabo on 2007-07-19
I found the answer:

You need apache 2 up and running in order for Tomcat to work. 

and

J2SE SDK and Java JDK are not the same although I thought they were supposed to be the same.

The Java errors I had was because I was using 
j2sdk-1_4_2_15-linux-i586.bin instead of jdk-6u2-linux-i586.bin

---

### Post by rabideau on 2007-07-23
Thank you Gary...

This was a wonderful help.  The only small point noobs like me need to know is that after editing the .bashrc you need to log-out and login again.

I also found it much better to use nano as the editor.. gedit seemed to leave a few hidden characters that caused the password file to burp.  

Anyway things are perfect!   THANKS!!!!!!!!:guitar:

---

### Post by mwolfe on 2007-08-10
you can actually reload your .bashrc without logging out/in
you just type
source .bashrc in your home directory,
(you can source any script that way)
however i think you need to log out and back in so that the stuff from /etc/environment take effect.

---

### Post by mohtasham1983 on 2007-08-21
Very nice tutorial.

For those who have problem finding jdk  you can download it here:
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

You don't need to restart your computer at all. Just write export and the rest of commands which were supposed to be written in those configuration files.


Thanks again for great tutorial.

---

### Post by suparoek on 2007-09-30
> **ahlandberg said:**
> Problem with Environment Variables:

Upon starting Tomcat with sudo /usr/share/tomcat6/bin/./startup.sh 

I get the following message:

ahlandberg@ubuntu610:/usr/lib$ sudo /usr/share/tomcat6/bin/./startup.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

I followed all the above instructions (except the Java setup, as I already had it installed).

My edited files look as follows:

#/etc/environment

CLASSPATH=.:/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/bin
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_AU.UTF-8"


#~/.bashrc

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
export HISTCONTROL=ignoredups

# Tomcat
[B]export JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11
export PATH=$PATH:$JAVA_HOME/bin
[/B]

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
    ;;
esac

# Comment in the above and uncomment this below for a color prompt
#PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'
    ;;
*)
    ;;
esac

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#    . ~/.bash_aliases
#fi

# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi

# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
#alias l='ls -CF'

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi





--

I am new to Linux, and appreciate any help!

Thanks in advance!

Anders



I have got same this problem link this

[I]Upon starting Tomcat with sudo /usr/share/tomcat6/bin/./startup.sh 

I get the following message:

ahlandberg@ubuntu610:/usr/lib$ sudo /usr/share/tomcat6/bin/./startup.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program[/I]


I try to restart machine then I type [http://localhost:8080](http://localhost:8080), so tomcat was runing.

I am not 100% sure this solution will work for you, but just try

---

### Post by voltage on 2008-06-12
> **cuongnhc said:**
> oh i found it, had no apache2 installed :)

can i install tomcat6 instate of apache2 ?

---

