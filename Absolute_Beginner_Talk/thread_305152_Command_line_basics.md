---
title: "Command line basics"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by baskinalaskin on 2006-11-22
Where can I find a good tutorial on linux commands in general, and on effectively using/configuring file system permissions. Have been searching the forums and on google, but I keep going in circles.

I'm running 6.10 / Edgy with the gnome GUI

My main issues (somewhat related):
*How to find/configure programs running in the background.
*How do users, groups, files, and folders relate to each other (in english, not wrwxwr...)
*Setting up SSH server and knowing my connections are secure
*Adding directories to user logins through FTPD

Another idea, besides the forums, is there a wiki-style information library for ubuntu?  With a drill down type of capibility?  If not, we should start one.

Thanks, and please post any good links you know of!

BaskinAlaskin

---

### Post by mssever on 2006-11-22
The first site that comes to mind is [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by ReaderRat on 2006-11-22
[** The Terminal/Konsole**](http://www.psychocats.net/ubuntu/terminal)
[**Alphabetical Commands**](http://www.ss64.com/bash/)
[**Linux In A Nutshell**](http://www.linuxdevcenter.com/linux/cmd/)

---

### Post by mssever on 2006-11-22
When it comes to SSH, install openssh-server. The default confic is quite secure, but you can tweak the settings in /etc/ssh/sshd_config.

---

### Post by IYY on 2006-11-22
> *How to find/configure programs running in the background.

Not sure exactly what you mean... To see the running programs, you can use 
```

top
```

or

```
ps aux
```

(ps is the command. aux is a set of arguments that gives an output you might be interested in. Read the manual for more options)

```
*How do users, groups, files, and folders relate to each other (in english, not wrwxwr...)
```

Users belong to groups (see the file /etc/group for a listing of all groups and their users). Every file has an owner and a creator (the two names you see with ls -l). rwxrwxrwx is nothing to be afraid of. It's just the permissions for user, group, and others. 'user' means the owner of the file. 'group' means the group to which the owner belongs. 'other' means all other users on the system. r means read, w means write and x means execute. 

To change the owner of a file/directory, use chown. To change permissions, use chmod <user/group/other>+<r/w/x> filename. For example, **chmod u+x file.txt** will give the user (owner) execute permissions.  

```
*Setting up SSH server and knowing my connections are secure
```

Just installing an SSH server like Dropbear (sudo apt-get install dropbear) should be enough. Of course, you must make sure that your usernames and passwords are strong, because people *will* try to crack them.

```
*Adding directories to user logins through FTPD
```

If you've installed FTPD and enabled users to log in, they should be allowed to create directories.

---

### Post by baskinalaskin on 2006-11-22
Thx for the qwk reply!  I'm still a noob, know I just need to dig furthur into the system to learn it better.  Thanks for your patience.. 

SSH: I have (or think I have) public keys setup on client/server.   But my private key (client) is rejected by my server, and I can still log in.  Can username/password be seen when transmitted across the www?  (only on my intranet right now)

FTP: I want to login to my server, to configure my homepage.  How do I give permissions to my var/www/ directory, to my FTP web admin username, to access via FTP.  In other words, I want to tap into the MP of my LAMP via FTP, by editing my HTML pages stored in /var/www/.

---

### Post by mssever on 2006-11-22
> **IYY said:**
> Just installing an SSH server like Dropbear (sudo apt-get install dropbear) should be enough. Of course, you must make sure that your usernames and passwords are strong, because people *will* try to crack them.If youre concerned about security, I would recommend openssh over dropbear, because openssh is in the main repository. That means that its fully supported by Canonical and youll get timely security updates. With packages from the universe, you just dont know...

---

### Post by mssever on 2006-11-22
> **baskinalaskin said:**
> SSH: I have (or think I have) public keys setup on client/server.   But my private key (client) is rejected by my server, and I can still log in.  Can username/password be seen when transmitted across the www?  (only on my intranet right now)

SSH doesnt send anything in cleartext. Its all encrypted. But check the file permisions. One error there and the server will reject your key.

Once you get your key working, you can actually disable password logins if you want.

To log in and edit your pages, I think that ftp is unnecessary. You can use ssh instead. Ive never had a need to run an ftp server. Besides, ftp is insecure. passwords and everything are transmitted in cleartext.

---

### Post by baskinalaskin on 2006-11-22
Here's the sequence:
1.)Created a public key and copied to proper directories on client/server
2.)Execute putty.exe on my windows box (client), with private key loaded
3.)Log into server IP address via client, and get "Server rejected our key"
4.)Enter linux username/pw, and get logged in to terminal, no problem.

How can I tell what's going on in my server?  Ex.: How do I tell who is logged in and what programs are running?

---

### Post by baskinalaskin on 2006-11-22
Also, thanks for the great web links, really appreciate it!  And thanks for the very quick replys!

BaskinAlaskin

---

### Post by mssever on 2006-11-22
> **baskinalaskin said:**
> Here's the sequence:
1.)Created a public key and copied to proper directories on client/server
2.)Execute putty.exe on my windows box (client), with private key loaded
3.)Log into server IP address via client, and get "Server rejected our key"
4.)Enter linux username/pw, and get logged in to terminal, no problem.
cd to ~/.ssh (~ is an abbreviation for your home directory). All files in that directory **must** have 600 permissions (-rw-------) or the server will reject the keys. Do ls -l to check, chmod 600 filename to change it.
> How can I tell what's going on in my server?  Ex.: How do I tell who is logged in and what programs are running?Type w to see who's currently logged in. Type top for the processes using the most resources. Type ps -ef | grep searchpattern for info about a specific process. I've got a shell script that simplifies the latter. Save the following as /usr/local/bin/p and make it executable (chmod +x /usr/local/bin/p): ```
#!/bin/bash
#
# Shortcut to ps -ef | grep foo

GREP="|grep"
CMD="ps -ef"
CMD2=
finalStr=

printHelp() {
    echo -e "Shortcut to \"ps -ef | grep foo\"\n"
    echo "Usage: $(basename "$0") [-i] [-v] pattern1 [pattern2 [pattern3 [...]]]"
    echo "-i: case-insensitive grep"
    echo "-v: inverse grep: return lines that do NOT match the pattern"
    exit
}

for i in "$@"; do
    getopts ivh option
    #echo -e "i=${i}\noption=${option}\n"
    if   [ $option == i ]; then GREP="${GREP} -i"
    elif [ $option == v ]; then GREP="${GREP} -v"
    elif [ $option == h -o "$i" == "--help" ]; then printHelp; fi
done

for i in "$@"; do
    if [ "$i" == "-i" -o "$i" == "-v" -o "$i" == "-vi" -o "$i" == "-iv" ]; then shift
    else break; fi
done

#echo "Args: $@"

for i in "$@"; do CMD2="${CMD2}${GREP} \"$i\""; done

finalStr="${CMD}${CMD2}"

eval $finalStr
#echo $finalStr
```To use it, type ```
p search_term_1 search_term_2 ...
```Type "p --help" for more options.

---

