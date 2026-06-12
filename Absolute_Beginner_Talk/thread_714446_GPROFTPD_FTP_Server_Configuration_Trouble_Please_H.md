---
title: "GPROFTPD FTP Server Configuration Trouble: Please Help!"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-03-03
Okay. First off, let me say that this is very important, as I have to get my FTP server up as fast as possible. ANY help at all will be greatly appreciated.

So, First off, I must admit that I'm not really sure how to do this, and can't say that I ever have before (on Ubuntu). I got things looking okay (I think), but every time I attempt to activate the server, I get this error:

```
 - IPv4 getaddrinfo 'compy' error: No address associated with hostname
 - warning: unable to determine IP address of 'compy'
 - error: no valid servers configured
 - Fatal: error processing configuration file '/etc/proftpd/proftpd.conf'
```

'compy' is the name of my computer.
Something you may want to know before continuing: I'm behind an NAT router.

This is what my configuration file looks like:

```

ServerType standalone
DefaultServer on
Umask 022
ServerName "0.0.0.0"
ServerIdent on "Christopher's Server"
ServerAdmin Sinkingships7@aim.com
IdentLookups off
UseReverseDNS off
Port 7542
PassivePorts 49152 65534
MasqueradeAddress 192.168.0.1
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 30
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
RequireValidShell off
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_homedir_path /var/ftp
#gp_html_path /var/www/html/ftp.htm
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  DenyALL
</Limit>

```

Again, thank you so much to anyone that helps.

This is very important to me and I've been looking everywhere and trying to figure out how to do this for days.

Please help me!!!!

---

### Post by Sinkingships7 on 2008-03-03
anyone? please?

---

### Post by Sinkingships7 on 2008-03-03
bump

---

### Post by freebeer on 2008-03-03
When you get that error, what are you doing?  Are you on the server itself, or using an ftp client from another machine from within the local area network? From the internet side of the router?

When behind a router, you'll have to forward the appropriate ports from the router to the ftp server (and the ftp server should have a static IP address).  Initially, you also want to connect using ACTIVE mode.  Passive mode is more difficult to set up, and not all routers, apparently, can support forwarding through a large range of passive ports.  So use ACTIVE mode for now.

---

### Post by Sinkingships7 on 2008-03-03
> **freebeer said:**
> When you get that error, what are you doing?  Are you on the server itself, or using an ftp client from another machine from within the local area network? From the internet side of the router?

When behind a router, you'll have to forward the appropriate ports from the router to the ftp server (and the ftp server should have a static IP address).  Initially, you also want to connect using ACTIVE mode.  Passive mode is more difficult to set up, and not all routers, apparently, can support forwarding through a large range of passive ports.  So use ACTIVE mode for now.

I get that error when trying to activate the server on the server software. I haven't yet tried connecting on another computer with a client, as I see little point in doing that while I can't get the server to even turn on. This is all being done behind the router.

I forwarded the port I'm using (7542) in my router's configuration page.

What I don't understand (from what you said) is:
a.) How to set the FTP server to have a static IP, or what I should do with it.
b.) How to set my mode (passive or active).

---

### Post by freebeer on 2008-03-04
> **Sinkingships7 said:**
> 
What I don't understand (from what you said) is:
a.) How to set the FTP server to have a static IP, or what I should do with it.
b.) How to set my mode (passive or active).

B is done from the ftp client itself, so let's leave that for the time being.

for A) Go into System -> Administration -> Network.  Click on your ethernet connection then click on Properties.  Change it to a static IP and give it a unique IP address (probably one high enough that your router won't ever give that address to another machine).  For instance, I gave mine an IP address of 192.168.1.150 (with the router doling out IP addresses for other computers starting at .100)

Hope that help some.

---

