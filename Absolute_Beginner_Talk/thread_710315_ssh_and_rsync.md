---
title: "ssh and rsync"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by nomad1970 on 2008-02-28
Hi,

I have a machine at work, and one at home.  I'd like to use ssh and rsync to backup from work to home machine.  Both run ubuntu server 7.10.

I've followed through the article here:

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

And for the most part figured it out.

What I don't understand, or more what I'd 'like to understand, is what this particular script does, how it works:

What is *\(*), and *\;*, esac?

Just a brief breakdown of some of these lines would be much appreciated!  

Thanks

#!/bin/sh

case "$SSH_ORIGINAL_COMMAND" in
*\&*)
echo "Rejected"
;;
*\(*)
echo "Rejected"
;;
*\{*)
echo "Rejected"
;;
*\;*)
echo "Rejected"
;;
*\<*)
echo "Rejected"
;;
*\`*)
echo "Rejected"
;;
rsync\ --server*)
$SSH_ORIGINAL_COMMAND
;;
*)
echo "Rejected"
;;
esac

---

### Post by justleen on 2008-02-28
the *\(*) are regular expression for pattern matching.
its matching al the ödd"chars,  { } ; < etc, if its matches, its spews am error.


esac is the end of the case statement.. bash has a habit of reversing statements..
if => fi
case => esac

---

### Post by nomad1970 on 2008-02-28
Thanks for the response.  

How does this increase security?

I've seen this script all over the net, but not much explanation - or is it blatantly obvious to all but me..  :)

Thanks.

---

### Post by Oldsoldier2003 on 2008-02-28
> **nomad1970 said:**
> Thanks for the response.  

How does this increase security?

I've seen this script all over the net, but not much explanation - or is it blatantly obvious to all but me..  :)

Thanks.
Using rysnc doesn't increase security,** using SSH does** since all transactions are encrypted. FTP and telnet send your username and password in plain text mode.

---

### Post by nomad1970 on 2008-02-28
> **Oldsoldier2003 said:**
> Using rysnc doesn't increase security,** using SSH does** since all transactions are encrypted. FTP and telnet send your username and password in plain text mode.

Thanks, I understand that SSH does, what I'm trying to understand is how the script above factors into security when using rsync over ssh.

---

### Post by Oldsoldier2003 on 2008-02-28
> **nomad1970 said:**
> Thanks, I understand that SSH does, what I'm trying to understand is how the script above factors into security when using rsync over ssh.

Mostly it doesn''t ( unless disaster strikes), it's a backup script he uses to make a local copy of some logging mail and configuration information from some remote servers. kinda like running a partial backup and carrying the backup back home with you- just never have to leave your desk.

Also the scripts and instructions are for Redhat based systems, Ubuntu is a debian based distro, but the general ifo is all good. you might have to make some allowances for the difference between RH and Debian tools.

---

### Post by nomad1970 on 2008-02-28
Thanks,

I found the explanation in the footnotes, for anyone else out there:

By the time the 'validate-rsync' script runs, a SSH connection has been made with the SSH key you associated with this command in the 'authorized_keys' file. The script basically tries to return 'Rejected' to anything other than a command that starts with "rsync --server", which is what rsync over ssh does on the other end of the connection. I found this out by running 'ps auxw | grep rsync' on the remote end of the connection after initializing a long running rsync job, but an rsync pro said you can add '-v -v -n' to your command line options for rsync and it will display the command it will use on the server end, so use that to make your script command more specific if you wish. The first six 'Rejected' lines try to elimate shell symbols that will allow a person to execute more than one command within a session (for example, a short rsync and some naughty command you don't want running remotely).

---

