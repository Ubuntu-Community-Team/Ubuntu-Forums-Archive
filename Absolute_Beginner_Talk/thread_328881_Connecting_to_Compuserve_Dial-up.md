---
title: "Connecting to Compuserve Dial-up"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by PaperPilot on 2006-12-31
Hi All:

I have been trying to connect to Compuserve with a dial-up modem.  I installed gnome-ppp and it connects all right, but I still need to run the connection script before I can use the service.  The log shows I am getting the proper challenge.  How can I set up the proper replies?

Thanks in advance.

---

### Post by ingo on 2007-01-02
I have a friend who is about to face the same problem (but not yet) so please keep me informed in case of any developments :)

---

### Post by seijuro on 2007-01-02
what script are you running? if you run sudo pppconfig and set up a profile there you should be able to just do pon/poff <profile-name> to connect/disconnect to your isp I use pennswoods dialup with kppp for most of the time and use pon/poff when kppp starts flaking out to see if I need to restart my modem driver.

---

### Post by PaperPilot on 2007-01-02
I am using gnome-ppp.  In a different distribution, I used kppp and that was all right.  Gnome-ppp has space for a reply line, but it takes several challenges and replies before I am connected.  I don't know if I can gnome-ppp to do handle multipule replies.

---

### Post by PaperPilot on 2007-01-25
I found the way.  It is described in [HTML]http://ringlord.com/publications/ppp-automation/[/HTML]

Keep in mind these three points:

1) Each file needs the 755 permissions.

2) replace the ppp-on-dialer file with:
```

#!/bin/sh
#
# This script performs the login authentication with your ISP. Notice that we're
# creating the file /etc/ppp/ppp-chat on the fly; if we passed account/password
# parameters on the command line (which is certainly possible) a savvy user on
# our network could snoop ps(1) to view the chat program's command line parameters
# and discover the login/password at our ISP's. Use of a script avoids that risk.
#
cat >/etc/ppp/ppp-chat <<EOF
        TIMEOUT            3
        ABORT               '\nBUSY\r'
        ABORT               '\nNO ANSWER\r'
        ABORT               '\nRINGING\r\n\r\nRINGING\r'
        ''                        ATS0=0Q0V1&C1&D2\r
        'OK-+++\c-OK'   ATH1
        TIMEOUT            30
        OK                     ATDT$TELEPHONE
        CONNECT           ''
        TIMEOUT           3
        Name:              CIS
        ID:                   $ACCOUNT/go:pppconnect
        word:                $PASSWORD
        TIMEOUT          5
EOF
exec /usr/sbin/chat -f /etc/ppp/ppp-chat

```

3) If you get the files from a windows machine, you must remove the carriage returns (displayed as ^M in error messages).  You can delete carriage return with the following script:

         tr -d '\r' < ppp-on-dialer.old > ppp-on-dialer


That is all there is to it.

---

### Post by ingo on 2007-01-25
right, sounds a breeze ;)

i've been telling my mate he should get broadband, I think that'll do the trick! 

but thanks very much for your help, paperpilot! good of you to share knowledge.

---

