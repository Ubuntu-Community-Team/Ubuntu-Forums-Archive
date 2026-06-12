---
title: "I require SMTP behind my ISP firewall"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Hasen_A on 2007-10-15
Hello,

I am sitting in my university dorm with an ISP that is now blocking very many ports not allowing me to send my emails using smtp over port 25. I have been reading and searching for 2 hours now and haven't really found a solution. I found infos on postfix, which requires an exterior server listening on other ports for rerouting the mail, if I understood the concept correctly. This however is not possible for me. I further don't know which ports are randomly available to me, ```
$netstat -l 
```delivers the following

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:2208          *:*                     LISTEN     
tcp        0      0 *:nfs                   *:*                     LISTEN     
tcp        0      0 *:35620                 *:*                     LISTEN     
tcp        0      0 *:swat                  *:*                     LISTEN     
tcp        0      0 *:netbios-ssn           *:*                     LISTEN     
tcp        0      0 *:52621                 *:*                     LISTEN     
tcp        0      0 *:sunrpc                *:*                     LISTEN     
tcp        0      0 localhost:8118          *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 localhost:9050          *:*                     LISTEN     
tcp        0      0 *:35613                 *:*                     LISTEN     
tcp        0      0 *:microsoft-ds          *:*                     LISTEN     
tcp        0      0 localhost:2207          *:*                     LISTEN     
tcp6       0      0 *:5900                  *:*                     LISTEN     
tcp6       0      0 *:ssh                   *:*                     LISTEN     
udp        0      0 *:32768                 *:*                                
udp        0      0 *:nfs                   *:*                                
udp        0      0 *:898                   *:*                                
udp        0      0 *:32771                 *:*                                
udp        0      0 localhost:32776         *:*                                
udp        0      0 andy-laptop:netbios-ns  *:*                                
udp        0      0 169.254.9.13:netbios-ns *:*                                
udp        0      0 172.16.79.1:netbios-ns  *:*                                
udp        0      0 172.16.228.1:netbios-ns *:*                                
udp        0      0 *:netbios-ns            *:*                                
udp        0      0 andy-laptop:netbios-dgm *:*                                
udp        0      0 169.254.9.1:netbios-dgm *:*                                
udp        0      0 172.16.79.1:netbios-dgm *:*                                
udp        0      0 172.16.228.:netbios-dgm *:*                                
udp        0      0 *:netbios-dgm           *:*                                
udp        0      0 *:668                   *:*                                
udp        0      0 *:35613                 *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:bootpc                *:*                                
udp        0      0 *:sunrpc                *:*                                
udp        0      0 172.16.228.1:ntp        *:*                                
udp        0      0 172.16.79.1:ntp         *:*                                
udp        0      0 localhost:ntp           *:*                                
udp        0      0 *:ntp                   *:*                                
udp6       0      0 *:xdmcp                 *:*                                
udp6       0      0 fe80::250:56ff:fec0:ntp *:*                                
udp6       0      0 ip6-localhost:ntp       *:*                                
udp6       0      0 fe80::250:56ff:fec0:ntp *:*                                
udp6       0      0 *:ntp                   *:*                                
raw        0      0 *:icmp                  *:*                     7       
```

I would like to use my prior outgoing email servers: smtp.online.de and mail.gmx.de. Does someone have a solution?

Thanks
Andy

---

### Post by scrooge_74 on 2007-10-15
Try an Onion router 

[http://tor.eff.org/](http://tor.eff.org/)

Maybe you can work around the firewall this way ;)

---

### Post by [S|G] on 2007-10-15
Is your ISP blocking outgoing connections? To confirm that you should telnet your mail server on port 25, like this:

```
telnet mail.gmx.de 25
```

If you can't connect, it is indeed blocking your connections. Then you'd need to use an external proxy server to connect to the server.

Now, if you're trying to setup a mail server that listens to connections from the outside and receives mail, you can use port 587 (submission) instead of port 25. If that port is also blocked you should be able to use any port over 1024 to place your server on.

---

### Post by Hasen_A on 2007-10-16
Yes that's what I said: my **ISP is blocking port 25** as well as a whole lot of other ones. However, there is no possibility for me to create an outside server since I am staying in France on an exchange program. I am also not familiar with how to connect to other proxies using TOR. I have already installed TOR along with privoxy but do not know which proxies to use and how to set up the programs correctly.

It would also be great if I could get gaims MSN function to work again properly and if apt-get would start working again.

All was fine a week ago, but then the Internet Connection went down without any notice and when it went back up a lot of ports were closed and many of my programs no longer worked. The admin(s) here also do not answer to any questions via email. Sorta sucks.

In order to connect to the internet I have to: Connect to the wireless network, open a browser and hit a link. I am then forwarded to an intranet site where I must login using **user@school.fr** and password keeping the browser window open afterwards for all times. Then most internet applications in ubuntu/windows work, but sometimes if the browser crashes the internet does too. This causes a lot of problems.

Is there a worked around for the login to the proxy using a shell?

---

### Post by scrooge_74 on 2007-10-16
can you use a command line browser like w3m instead of the regular browser?

tutorial for tor

[http://ubuntuforums.org/showthread.php?t=10825&highlight=tor](http://ubuntuforums.org/showthread.php?t=10825&highlight=tor)

---

### Post by Hasen_A on 2007-10-19
If I follow that how-to I cannot, since I need to configure TOR and Privoxy further, since I am sitting behind a ISP proxy that is blocking almost all ports. I haven't found any good how-to for that. Do you know any good ones?

---

### Post by Hasen_A on 2007-10-22
> **scrooge_74 said:**
> can you use a command line browser like w3m instead of the regular browser?

tutorial for tor

[http://ubuntuforums.org/showthread.php?t=10825&highlight=tor](http://ubuntuforums.org/showthread.php?t=10825&highlight=tor)

Well I set up tor and privoxy following the internet docs of both sites using some of my own tuition, which I think is part of the reason its not working yet :).

Here is my tor logfile, I am not 100% sure of the proxy adress (cache-1.in.crous-toulouse.fr). How do I check this? User and Password have been omitted to remain anonymus:
```
more /var/log/tor/notices.log 
Oct 23 01:11:02.816 [notice] Tor 0.1.2.17 opening new log file.
Oct 23 01:11:03.244 [notice] I learned some more directory information, but not enough to build a circuit.
Oct 23 01:17:09.600 [warn] Received http status code 404 ("Not Found") from server '86.59.21.38:80' while fetching "/tor/status/fp/38D4F5FCF7B1023228B895EA56EDE7D5CCDCAF32+719BE45DE224B607C53707D0E2143E2D423E74
CF+7EA6EAD6FD83083C538F44038BBFA077587DD755+847B1F850344D7876491A54892F904934E4EB85D+FFCB46DB1339DA84674C70D7CB586434C4370441.z". I'll try again soon.
Oct 23 01:18:10.554 [warn] Received http status code 404 ("Not Found") from server '86.59.21.38:80' while fetching "/tor/status/fp/38D4F5FCF7B1023228B895EA56EDE7D5CCDCAF32+719BE45DE224B607C53707D0E2143E2D423E74
CF+7EA6EAD6FD83083C538F44038BBFA077587DD755+847B1F850344D7876491A54892F904934E4EB85D+FFCB46DB1339DA84674C70D7CB586434C4370441.z". I'll try again soon.
Oct 23 01:20:00.683 [notice] Interrupt: exiting cleanly.
Oct 23 01:20:02.792 [notice] Tor 0.1.2.17 opening log file.
Oct 23 01:20:03.178 [notice] I learned some more directory information, but not enough to build a circuit.
Oct 23 01:21:04.341 [warn] Received http status code 404 ("Not Found") from server '194.109.206.212:80' while fetching "/tor/status/fp/38D4F5FCF7B1023228B895EA56EDE7D5CCDCAF32+719BE45DE224B607C53707D0E2143E2D42
3E74CF+7EA6EAD6FD83083C538F44038BBFA077587DD755+847B1F850344D7876491A54892F904934E4EB85D+FFCB46DB1339DA84674C70D7CB586434C4370441.z". I'll try again soon.
```

Torrc configfile
```
## Configuration file for a typical Tor user
## Last updated 8 October 2006 for Tor 0.1.2.3-alpha.
## (May or may not work for older or newer versions of Tor.)
##
## Lines that begin with "## " try to explain what's going on. Lines
## that begin with just "#" are disabled commands: you can enable them
## by removing the "#" symbol.
##
## See the man page, or http://tor.eff.org/tor-manual-cvs.html, for more
## options you can use in this file.
##
## On Unix, Tor will look for this file in someplace like "~/.tor/torrc" or
## "/etc/torrc"
##
## On Windows, Tor will look for the configuration file in someplace like
## "Application Data\tor\torrc" or "Application Data\<username>\tor\torrc"
##
## With the default Mac OS X installer, Tor will look in ~/.tor/torrc or
## /Library/Tor/torrc


## Replace this with "SocksPort 0" if you plan to run Tor only as a
## server, and not make any local application connections yourself.
SocksPort 9050 # what port to open for local application connections
SocksListenAddress 127.0.0.1 # accept connections only from localhost
#SocksListenAddress 192.168.0.1:9100 # listen on this IP:port also

## Entry policies to allow/deny SOCKS requests based on IP address.
## First entry that matches wins. If no SocksPolicy is set, we accept
## all (and only) requests from SocksListenAddress.
#SocksPolicy accept 192.168.0.0/16
#SocksPolicy reject *

## Logs go to stdout at level "notice" unless redirected by something
## else, like one of the below lines. You can have as many Log lines as
## you want.
##
## We advise using "notice" in most cases, since anything more verbose
## may provide sensitive information to an attacker who obtains the logs.
##
## Send all messages of level 'notice' or higher to /var/log/tor/notices.log
#Log notice file /var/log/tor/notices.log

Log notice file /var/log/tor/notices.log

## Send every possible message to /var/log/tor/debug.log
#Log debug file /var/log/tor/debug.log
## Use the system log instead of Tor's logfiles
#Log notice syslog
## To send all messages to stderr:
#Log debug stderr

## Uncomment this to start the process in the background... or use
## --runasdaemon 1 on the command line. This is ignored on Windows;
## see the FAQ entry if you want Tor to run as an NT service.
#RunAsDaemon 1

## The directory for keeping all the keys/etc. By default, we store
## things in $HOME/.tor on Unix, and in Application Data\tor on Windows.
#DataDirectory /var/lib/tor

## The port on which Tor will listen for local connections from Tor
## controller applications, as documented in control-spec.txt.
#ControlPort 9051

############### This section is just for location-hidden services ###

## Once you have configured a hidden service, you can look at the
## contents of the file ".../hidden_service/hostname" for the address
## to tell people.
##
## HiddenServicePort x y:z says to redirect requests on port x to the
## address y:z.

#HiddenServiceDir /var/lib/tor/hidden_service/
#HiddenServicePort 80 127.0.0.1:80

#HiddenServiceDir /var/lib/tor/other_hidden_service/
#HiddenServicePort 80 127.0.0.1:80
#HiddenServicePort 22 127.0.0.1:22

################ This section is just for servers #####################

## NOTE: If you enable these, you should consider mailing the contents
## of the "fingerprint" file to the tor-ops, so nobody else can pick
## your nickname and use a different key. See
## http://tor.eff.org/docs/tor-doc-server.html for details.

## Required: A unique handle for your server.
#Nickname ididnteditheconfig

## The IP or FQDN for your server. Leave commented out and Tor will guess.
#Address noname.example.com

## Define these to limit your bandwidth usage. Note that BandwidthRate
## must be at least 20 KB.
#BandwidthRate 100 KB      # Throttle traffic to 100KB/s (800Kbps)
#BandwidthBurst 200 KB     # But allow bursts up to 200KB/s (1600Kbps)

## Contact info to be published in the directory, so we can contact you
## if your server is misconfigured or something else goes wrong.
#ContactInfo Random Person <nobody AT example dot com>
## You might also include your PGP or GPG fingerprint if you have one:
#ContactInfo 1234D/FFFFFFFF Random Person <nobody AT example dot com>

## Required: what port to advertise for Tor connections.
#ORPort 9001
## If you want to listen on a port other than the one advertised
## in ORPort (e.g. to advertise 443 but bind to 9090), uncomment the
## line below too. You'll need to do ipchains or other port forwarding
## yourself to make this work.
#ORListenAddress 0.0.0.0:9090

## Uncomment this to mirror the directory for others. Please do
## if you have enough bandwidth: see the bottom of
## http://wiki.noreply.org/noreply/TheOnionRouter/TorFAQ#LimitBandwidth
#DirPort 9030 # what port to advertise for directory connections
## If you want to listen on a port other than the one advertised
## in DirPort (e.g. to advertise 80 but bind to 9091), uncomment the line
## below too. You'll need to do ipchains or other port forwarding yourself
## to make this work.
#DirListenAddress 0.0.0.0:9091

## Uncomment this if you run more than one Tor server, and add the
## nickname of each Tor server you control, even if they're on different
## networks. You declare it here so Tor clients can avoid using more than
## one of your servers in a single circuit.
#MyFamily nickname1,nickname2,...

## A comma-separated list of exit policies. They're considered first
## to last, and the first match wins. If you want to _replace_
## the default exit policy, end this with either a reject *:* or an
## accept *:*. Otherwise, you're _augmenting_ (prepending to) the
## default exit policy. Leave commented to just use the default, which is
## available in the man page or at http://tor.eff.org/documentation.html
##
## Look at http://tor.eff.org/faq-abuse.html#TypicalAbuses
## for issues you might encounter if you use the default exit policy.
##
## If certain IPs and ports are blocked externally, e.g. by your firewall,
## you should update your exit policy to reflect this -- otherwise Tor
## users will be told that those destinations are down.
##
#ExitPolicy accept *:6660-6667,reject *:* # allow irc ports but no more
#ExitPolicy accept *:119 # accept nntp as well as default exit policy
#ExitPolicy reject *:* # no exits allowed

#meine einstellungen
FascistFirewall 1
ReachableDirAddresses *:80
ReachableORAddresses *:443


HttpsProxy cache-1.in.crous-toulouse.fr
#10.251.151.4:8080
HttpsProxyAuthenticator [user_hereneglected]@enseeiht.fr:[password_hereneglected]
```

Privoxy Configfile
```
#        Sample Configuration File for Privoxy
#
#  Id: config,v
#
#  Copyright (C) 2001-2006 Privoxy Developers http://privoxy.org
#
####################################################################
#                                                                  #
#                      Table of Contents                           #
#                                                                  #
#        I. INTRODUCTION                                           #
#       II. FORMAT OF THE CONFIGURATION FILE                       #
#                                                                  #
#        1. LOCAL SET-UP DOCUMENTATION                             #
#        2. CONFIGURATION AND LOG FILE LOCATIONS                   #
#        3. DEBUGGING                                              #
#        4. ACCESS CONTROL AND SECURITY                            #
#        5. FORWARDING                                             #
#        6. WINDOWS GUI OPTIONS                                    #
#                                                                  #
####################################################################
#
#
#  I. INTRODUCTION
#   ===============
#
#  This file holds the Privoxy configuration. If you modify this file,
#  you will need to send a couple of requests (of any kind) to the
#  proxy before any changes take effect.
#
#  When starting Privoxy on Unix systems, give the name of this file as
#  an argument. On Windows systems, Privoxy will look for this file
#  with the name 'config.txt' in the same directory where Privoxy
#  is installed.
#
#
#  II. FORMAT OF THE CONFIGURATION FILE
#  ====================================
#
#  Configuration lines consist of an initial keyword followed by a
#  list of values, all separated by whitespace (any number of spaces
#  or tabs). For example,
#
#  actionsfile default.action
#
#  Indicates that the actionsfile is named 'default.action'.
#
#  The '#' indicates a comment. Any part of a line following a '#'
#  is ignored, except if the '#' is preceded by a '\'.
#
#  Thus, by placing a # at the start of an existing configuration line,
#  you can make it a comment and it will be treated as if it weren't
#  there. This is called "commenting out" an option and can be useful.
#
#  Note that commenting out and option and leaving it at its default
#  are two completely different things! Most options behave very
#  differently when unset.  See the the "Effect if unset" explanation
#  in each option's description for details.
#
#  Long lines can be continued on the next line by using a `\' as the
#  last character.
#

#
#  1. LOCAL SET-UP DOCUMENTATION
#  =============================
#
#  If you intend to operate Privoxy for more users than just yourself,
#  it might be a good idea to let them know how to reach you, what
#  you block and why you do that, your policies, etc.
#

#
#  1.1. user-manual
#  ================
#
#  Specifies:
#
#      Location of the Privoxy User Manual.
#
#  Type of value:
#
#      A fully qualified URI
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      http://www.privoxy.org/version/user-manual/ will be used,
#      where version is the Privoxy version.
#
#  Notes:
#
#      The User Manual URI is the single best source of information on
#      Privoxy, and is used for help links from some of the internal
#      CGI pages. The manual itself is normally packaged with the
#      binary distributions, so you probably want to set this to
#      a locally installed copy. For multi-user setups, you could
#      provide a copy on a local webserver for all your users and use
#      the corresponding URL here.
#
#      Examples:
#
#      The best all purpose solution is simply to put the full local
#      PATH to where the User Manual is located:
#
#        user-manual  /usr/share/doc/privoxy/user-manual
#
#      The User Manual is then available to anyone with
#      access to the proxy, by following the built-in URL:
#      http://config.privoxy.org/user-manual/ (or the shortcut:
#      http://p.p/user-manual/).
#
#      If the documentation is not on the local system, it can be
#      accessed from a remote server, as:
#
#        user-manual  http://example.com/privoxy/user-manual/
#
#      WARNING!!!
#
#          If set, this option should be the first option in the config
#          file, because it is used while the config file is being read.
#
user-manual /usr/share/doc/privoxy/user-manual

#
#  1.2. trust-info-url
#  ===================
#
#  Specifies:
#
#      A URL to be displayed in the error page that users will see if
#      access to an untrusted page is denied.
#
#  Type of value:
#
#      URL
#
#  Default value:
#
#      Two example URL are provided
#
#  Effect if unset:
#
#      No links are displayed on the "untrusted" error page.
#
#  Notes:
#
#      The value of this option only matters if the experimental trust
#      mechanism has been activated. (See trustfile above.)
#
#      If you use the trust mechanism, it is a good idea to write
#      up some on-line documentation about your trust policy and to
#      specify the URL(s) here. Use multiple times for multiple URLs.
#
#      The URL(s) should be added to the trustfile as well, so users
#      don't end up locked out from the information on why they were
#      locked out in the first place!
#
#trust-info-url  http://www.example.com/why_we_block.html
#trust-info-url  http://www.example.com/what_we_allow.html

#
#  1.3. admin-address
#  ==================
#
#  Specifies:
#
#      An email address to reach the proxy administrator.
#
#  Type of value:
#
#      Email address
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      No email address is displayed on error pages and the CGI user
#      interface.
#
#  Notes:
#
#      If both admin-address and proxy-info-url are unset, the whole
#      "Local Privoxy Support" box on all generated pages will not
#      be shown.
#
#admin-address privoxy-admin@example.com

#
#  1.4. proxy-info-url
#  ===================
#
#  Specifies:
#
#      A URL to documentation about the local Privoxy setup,
#      configuration or policies.
#
#  Type of value:
#
#      URL
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      No link to local documentation is displayed on error pages and
#      the CGI user interface.
#
#  Notes:
#
#      If both admin-address and proxy-info-url are unset, the whole
#      "Local Privoxy Support" box on all generated pages will not
#      be shown.
#
#      This URL shouldn't be blocked ;-)
#
#proxy-info-url http://www.example.com/proxy-service.html

#
#  2. CONFIGURATION AND LOG FILE LOCATIONS
#  =======================================
#
#  Privoxy can (and normally does) use a number of other files for
#  additional configuration, help and logging. This section of the
#  configuration file tells Privoxy where to find those other files.
#
#  The user running Privoxy, must have read permission for all
#  configuration files, and write permission to any files that would
#  be modified, such as log files and actions files.
#

#
#  2.1. confdir
#  ============
#
#  Specifies:
#
#      The directory where the other configuration files are located
#
#  Type of value:
#
#      Path name
#
#  Default value:
#
#      /etc/privoxy (Unix) or Privoxy installation dir (Windows)
#
#  Effect if unset:
#
#      Mandatory
#
#  Notes:
#
#      No trailing "/", please
#
#      When development goes modular and multi-user, the blocker,
#      filter, and per-user config will be stored in subdirectories of
#      "confdir". For now, the configuration directory structure is
#      flat, except for confdir/templates, where the HTML templates
#      for CGI output reside (e.g. Privoxy's 404 error page).
#
confdir /etc/privoxy

#
#  2.2. logdir
#  ===========
#
#  Specifies:
#
#      The directory where all logging takes place (i.e. where logfile
#      and jarfile are located)
#
#  Type of value:
#
#      Path name
#
#  Default value:
#
#      /var/log/privoxy (Unix) or Privoxy installation dir (Windows)
#
#  Effect if unset:
#
#      Mandatory
#
#  Notes:
#
#      No trailing "/", please
#
logdir /var/log/privoxy

#
#  2.3. actionsfile
#  ================
#
#  Specifies:
#
#      The actions file(s) to use
#
#  Type of value:
#
#      File name, relative to confdir, without the .action suffix
#
#  Default values:
#
#        standard     # Internal purposes, no editing recommended
#
#        default      # Main actions file
#
#        user         # User customizations
#
#  Effect if unset:
#
#      No actions are taken at all. Simple neutral proxying.
#
#  Notes:
#
#      Multiple actionsfile lines are permitted, and are in fact
#      recommended!
#
#      The default values include standard.action, which is used
#      for internal purposes and should be loaded, default.action,
#      which is the "main" actions file maintained by the developers,
#      and user.action, where you can make your personal additions.
#
#      Actions files are where all the per site and per URL
#      configuration is done for ad blocking, cookie management,
#      privacy considerations, etc. There is no point in using Privoxy
#      without at least one actions file.
#
actionsfile standard  # Internal purpose, recommended
actionsfile global    # Global default setting for all sites
actionsfile default   # Main actions file
actionsfile user      # User customizations

#
#  2.4. filterfile
#  ===============
#
#  Specifies:
#
#      The filter file(s) to use
#
#  Type of value:
#
#      File name, relative to confdir
#
#  Default value:
#
#      default.filter (Unix) or default.filter.txt (Windows)
#
#  Effect if unset:
#
#      No textual content filtering takes place, i.e. all +filter{name}
#      actions in the actions files are turned neutral.
#
#  Notes:
#
#      Multiple filterfile lines are permitted.
#
#      The filter files contain content modification rules that use
#      regular expressions. These rules permit powerful changes on
#      the content of Web pages, and optionally the headers as well,
#      e.g., you could disable your favorite JavaScript annoyances,
#      re-write the actual displayed text, or just have some fun
#      playing buzzword bingo with web pages.
#
#      The +filter{name} actions rely on the relevant filter (name)
#      to be defined in a filter file!
#
#      A pre-defined filter file called default.filter that contains a
#      number of useful filters for common problems is included in the
#      distribution. See the section on the filter action for a list.
#
#      It is recommended to place any locally adapted filters into a
#      separate file, such as user.filter.
#
filterfile default.filter
#filterfile user.filter      # User customizations

#
#  2.5. logfile
#  ============
#
#  Specifies:
#
#      The log file to use
#
#  Type of value:
#
#      File name, relative to logdir
#
#  Default value:
#
#      logfile (Unix) or privoxy.log (Windows)
#
#  Effect if unset:
#
#      No log file is used, all log messages go to the console (STDERR).
#
#  Notes:
#
#      The logfile is where all logging and error messages are
#      written. The level of detail and number of messages are set with
#      the debug option (see below).  The logfile can be useful for
#      tracking down a problem with Privoxy (e.g., it's not blocking
#      an ad you think it should block) but in most cases you probably
#      will never look at it.
#
#      Your logfile will grow indefinitely, and you will probably
#      want to periodically remove it. On Unix systems, you can do
#      this with a cron job (see "man cron"). For Red Hat, a logrotate
#      script has been included.
#
#      On SuSE Linux systems, you can place a line like
#      "/var/log/privoxy.* +1024k 644 nobody.nogroup" in /etc/logfiles,
#      with the effect that cron.daily will automatically archive,
#      gzip, and empty the log, when it exceeds 1M size.
#
#      Any log files must be writable by whatever user Privoxy is
#      being run as (default on UNIX, user id is "privoxy").
#
logfile logfile

#
#  2.6. jarfile
#  ============
#
#  Specifies:
#
#      The file to store intercepted cookies in
#
#  Type of value:
#
#      File name, relative to logdir
#
#  Default value:
#
#      Unset (commented out). When activated: jarfile (Unix) or
#      privoxy.jar (Windows)
#
#  Effect if unset:
#
#      Intercepted cookies are not stored in a dedicated log file.
#
#  Notes:
#
#      The jarfile may grow to ridiculous sizes over time.
#
#      If debug 8 (show header parsing) is enabled, cookies are written
#      to the logfile with the rest of the headers.
#
#jarfile jarfile

#
#  2.7. trustfile
#  ==============
#
#  Specifies:
#
#      The trust file to use
#
#  Type of value:
#
#      File name, relative to confdir
#
#  Default value:
#
#      Unset (commented out). When activated: trust (Unix) or trust.txt
#      (Windows)
#
#  Effect if unset:
#
#      The entire trust mechanism is turned off.
#
#  Notes:
#
#      The trust mechanism is an experimental feature for building
#      white-lists and should be used with care. It is NOT recommended
#      for the casual user.
#
#      If you specify a trust file, Privoxy will only allow access to
#      sites that are specified in the trustfile. Sites can be listed
#      in one of two ways:
#
#      Prepending a ~ character limits access to this site only (and
#      any sub-paths within this site), e.g. ~www.example.com.
#
#      Or, you can designate sites as trusted referrers, by prepending
#      the name with a + character. The effect is that access to
#      untrusted sites will be granted -- but only if a link from this
#      trusted referrer was used. The link target will then be added
#      to the "trustfile" so that future, direct accesses will be
#      granted. Sites added via this mechanism do not become trusted
#      referrers themselves (i.e. they are added with a ~ designation).
#
#      If you use the + operator in the trust file, it may grow
#      considerably over time.
#
#      It is recommended that Privoxy be compiled with the
#      --disable-force, --disable-toggle and --disable-editor options,
#      if this feature is to be used.
#
#      Possible applications include limiting Internet access for
#      children.
#
#trustfile trust

#
#  3. DEBUGGING
#  ============
#
#  These options are mainly useful when tracing a problem. Note that
#  you might also want to invoke Privoxy with the --no-daemon command
#  line option when debugging.
#

#
#  3.1. debug
#  ==========
#
#  Specifies:
#
#      Key values that determine what information gets logged to
#      the logfile.
#
#  Type of value:
#
#      Integer values
#
#  Default value:
#
#      12289 (i.e.: URLs plus informational and warning messages)
#
#  Effect if unset:
#
#      Nothing gets logged.
#
#  Notes:
#
#      The available debug levels are:
#
#          debug         1 # show each GET/POST/CONNECT request
#          debug         2 # show each connection status
#          debug         4 # show I/O status
#          debug         8 # show header parsing
#          debug        16 # log all data into the logfile
#          debug        32 # debug force feature
#          debug        64 # debug regular expression filter
#          debug       128 # debug fast redirects
#          debug       256 # debug GIF de-animation
#          debug       512 # Common Log Format
#          debug      1024 # debug kill pop-ups
#          debug      2048 # CGI user interface
#          debug      4096 # Startup banner and warnings.
#          debug      8192 # Non-fatal errors
#
#      To select multiple debug levels, you can either add them or
#      use multiple debug lines.
#
#      A debug level of 1 is informative because it will show you each
#      request as it happens. 1, 4096 and 8192 are highly recommended
#      so that you will notice when things go wrong. The other levels
#      are probably only of interest if you are hunting down a specific
#      problem. They can produce a hell of an output (especially 16).
#
#      The reporting of fatal errors (i.e. ones which crash Privoxy)
#      is always on and cannot be disabled.
#
#      If you want to use CLF (Common Log Format), you should set
#      "debug 512" ONLY and not enable anything else.
#
debug   1    # show each GET/POST/CONNECT request
debug   4096 # Startup banner and warnings
debug   8192 # Errors - *we highly recommended enabling this*

#
#  3.2. single-threaded
#  ====================
#
#  Specifies:
#
#      Whether to run only one server thread
#
#  Type of value:
#
#      None
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      Multi-threaded (or, where unavailable: forked) operation,
#      i.e. the ability to serve multiple requests simultaneously.
#
#  Notes:
#
#      This option is only there for debug purposes and you should
#      never need to use it. It will drastically reduce performance.
#
#single-threaded

#
#  4. ACCESS CONTROL AND SECURITY
#  ==============================
#
#  This section of the config file controls the security-relevant
#  aspects of Privoxy's configuration.
#

#
#  4.1. listen-address
#  ===================
#
#  Specifies:
#
#      The IP address and TCP port on which Privoxy will listen for
#      client requests.
#
#  Type of value:
#
#      [IP-Address]:Port
#
#  Default value:
#
#      127.0.0.1:8118
#
#  Effect if unset:
#
#      Bind to 127.0.0.1 (localhost), port 8118. This is suitable and
#      recommended for home users who run Privoxy on the same machine
#      as their browser.
#
#  Notes:
#
#      You will need to configure your browser(s) to this proxy address
#      and port.
#
#      If you already have another service running on port 8118, or
#      if you want to serve requests from other machines (e.g. on your
#      local network) as well, you will need to override the default.
#
#      If you leave out the IP address, Privoxy will bind to all
#      interfaces (addresses) on your machine and may become reachable
#      from the Internet. In that case, consider using access control
#      lists (ACL's, see below), and/or a firewall.
#
#      If you open Privoxy to untrusted users, you will also want
#      to turn off the enable-edit-actions and enable-remote-toggle
#      options!
#
#  Example:
#
#      Suppose you are running Privoxy on a machinelisten-address  127.0.0.1:8118
#	forward-socks4a / localhost:9050 .
#	which has the
#      address 192.168.0.1 on your local private network (192.168.0.0)
#      and has another outside connection with a different address. You
#      want it to serve requests from inside only:
#
#        listen-address  192.168.0.1:8118
#
listen-address  127.0.0.1:8118
forward-socks4a / localhost:9050 .

#
#  4.2. toggle
#  ===========
#
#  Specifies:
#
#      Initial state of "toggle" status
#
#  Type of value:
#
#      1 or 0
#
#  Default value:
#
#      1
#
#  Effect if unset:
#
#      Act as if toggled on
#
#  Notes:
#
#      If set to 0, Privoxy will start in "toggled off" mode,
#      i.e. behave like a normal, content-neutral proxy where all ad
#      blocking, filtering, etc are disabled. See enable-remote-toggle
#      below. This is not really useful anymore, since toggling is
#      much easier via the web interface than via editing the conf file.
#
#      The windows version will only display the toggle icon in the
#      system tray if this option is present.
#
toggle  1

#
#  4.3. enable-remote-toggle
#  =========================
#
#  Specifies:
#
#      Whether or not the web-based toggle feature may be used
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      1
#
#  Effect if unset:
#
#      The web-based toggle feature is disabled.
#
#  Notes:
#
#      When toggled off, Privoxy acts like a normal, content-neutral
#      proxy, i.e.  it acts as if none of the actions applied to
#      any URL.
#
#      For the time being, access to the toggle feature can not be
#      controlled separately by "ACLs" or HTTP authentication, so that
#      everybody who can access Privoxy (see "ACLs" and listen-address
#      above) can toggle it for all users. So this option is not
#      recommended for multi-user environments with untrusted users.
#
#      Note that you must have compiled Privoxy with support for this
#      feature, otherwise this option has no effect.
#
enable-remote-toggle  0

#
#  4.4. enable-remote-http-toggle
#  ==============================
#
#  Specifies:
#
#      Whether or not Privoxy recognizes special HTTP headers to change
#      its behaviour.
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      1
#
#  Effect if unset:
#
#      Privoxy ignores special HTTP headers.
#
#  Notes:
#
#      When toggled on, the client can change Privoxy's behaviour by
#      setting special HTTP headers. Currently the only supported
#      special header is "X-Filter: No", to disable filtering for
#      the ongoing request, even if it is enabled in one of the
#      action files.
#
#      If you are using Privoxy in a multi-user environment or with
#      untrustworthy clients and want to enforce filtering, you will
#      have to disable this option, otherwise you can ignore it.
#
enable-remote-http-toggle  1

#
#  4.5. enable-edit-actions
#  ========================
#
#  Specifies:
#
#      Whether or not the web-based actions file editor may be used
#
#  Type of value:
#
#      0 or 1
#
#  Default value:
#
#      1
#
#  Effect if unset:
#
#      The web-based actions file editor is disabled.
#
#  Notes:
#
#      For the time being, access to the editor can not be controlled
#      separately by "ACLs" or HTTP authentication, so that everybody
#      who can access Privoxy (see "ACLs" and listen-address above)
#      can modify its configuration for all users. So this option is
#      not recommended for multi-user environments with untrusted users.
#
#      Note that you must have compiled Privoxy with support for this
#      feature, otherwise this option has no effect.
#
enable-edit-actions 0

#
#  4.6. ACLs: permit-access and deny-access
#  ========================================
#
#  Specifies:
#
#      Who can access what.
#
#  Type of value:
#
#      src_addr[/src_masklen] [dst_addr[/dst_masklen]]
#
#      Where src_addr and dst_addr are IP addresses in dotted decimal
#      notation or valid DNS names, and src_masklen and dst_masklen are
#      subnet masks in CIDR notation, i.e. integer values from 2 to 30
#      representing the length (in bits) of the network address. The
#      masks and the whole destination part are optional.
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      Don't restrict access further than implied by listen-address
#
#  Notes:
#
#      Access controls are included at the request of ISPs and systems
#      administrators, and are not usually needed by individual
#      users. For a typical home user, it will normally suffice to
#      ensure that Privoxy only listens on the localhost (127.0.0.1)
#      or internal (home) network address by means of the listen-address
#      option.
#
#      Please see the warnings in the FAQ that this proxy is not
#      intended to be a substitute for a firewall or to encourage
#      anyone to defer addressing basic security weaknesses.
#
#      Multiple ACL lines are OK. If any ACLs are specified, then
#      the Privoxy talks only to IP addresses that match at least one
#      permit-access line and don't match any subsequent deny-access
#      line. In other words, the last match wins, with the default
#      being deny-access.
#
#      If Privoxy is using a forwarder (see forward below) for a
#      particular destination URL, the dst_addr that is examined is
#      the address of the forwarder and NOT the address of the ultimate
#      target. This is necessary because it may be impossible for the
#      local Privoxy to determine the IP address of the ultimate target
#      (that's often what gateways are used for).
#
#      You should prefer using IP addresses over DNS names, because
#      the address lookups take time. All DNS names must resolve! You
#      can not use domain patterns like "*.org" or partial domain
#      names. If a DNS name resolves to multiple IP addresses, only
#      the first one is used.
#
#      Denying access to particular sites by ACL may have undesired
#      side effects if the site in question is hosted on a machine
#      which also hosts other sites.
#
#  Examples:
#
#      Explicitly define the default behavior if no ACL and
#      listen-address are set: "localhost" is OK. The absence of a
#      dst_addr implies that all destination addresses are OK:
#
#        permit-access  localhost
#
#      Allow any host on the same class C subnet as www.privoxy.org
#      access to nothing but www.example.com:
#
#        permit-access  www.privoxy.org/24   www.example.com/32
#
#      Allow access from any host on the 26-bit subnet 192.168.45.64
#      to anywhere, with the exception that 192.168.45.73 may not
#      access www.dirty-stuff.example.com:
#
#        permit-access  192.168.45.64/26
#        deny-access    192.168.45.73     www.dirty-stuff.example.com
#

#
#  4.7. buffer-limit
#  =================
#
#  Specifies:
#
#      Maximum size of the buffer for content filtering.
#
#  Type of value:
#
#      Size in Kbytes
#
#  Default value:
#
#      4096
#
#  Effect if unset:
#
#      Use a 4MB (4096 KB) limit.
#
#  Notes:
#
#      For content filtering, i.e. the +filter and +deanimate-gif
#      actions, it is necessary that Privoxy buffers the entire document
#      body. This can be potentially dangerous, since a server could
#      just keep sending data indefinitely and wait for your RAM to
#      exhaust -- with nasty consequences.  Hence this option.
#
#      When a document buffer size reaches the buffer-limit, it is
#      flushed to the client unfiltered and no further attempt to filter
#      the rest of the document is made. Remember that there may be
#      multiple threads running, which might require up to buffer-limit
#      Kbytes each, unless you have enabled "single-threaded" above.
#
buffer-limit 4096

#
#  5. FORWARDING
#  =============
#
#  This feature allows routing of HTTP requests through a chain
#  of multiple proxies. It can be used to better protect privacy
#  and confidentiality when accessing specific domains by routing
#  requests to those domains through an anonymous public proxy.
#  Or to use a caching proxy to speed up browsing. Or chaining to
#  a parent proxy may be necessary because the machine that Privoxy
#  runs on has no direct Internet access.
#
#  Also specified here are SOCKS proxies. Privoxy supports the SOCKS
#  4 and SOCKS 4A protocols.
#

#
#  5.1. forward
#  ============
#
#  Specifies:
#
#      To which parent HTTP proxy specific requests should be routed.
#
#  Type of value:
#
#      target_pattern http_parent[:port]
#
#      where target_pattern is a URL pattern that specifies to which
#      requests (i.e. URLs) this forward rule shall apply. Use /
#      to denote "all URLs".  http_parent[:port] is the DNS name or
#      IP address of the parent HTTP proxy through which the requests
#      should be forwarded, optionally followed by its listening port
#      (default: 8080). Use a single dot (.) to denote "no forwarding".
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      Don't use parent HTTP proxies.
#
#  Notes:
#
#      If http_parent is ".", then requests are not forwarded to
#      another HTTP proxy but are made directly to the web servers.
#
#      Multiple lines are OK, they are checked in sequence, and the
#      last match wins.
#
#  Examples:
#
#      Everything goes to an example anonymizing proxy, except SSL on
#      port 443 (which it doesn't handle):
#
#        forward   /      anon-proxy.example.org:8080
#        forward   :443   .
#
#      Everything goes to our example ISP's caching proxy, except for
#      requests to that ISP's sites:
#
#        forward   /                  caching-proxy.example-isp.net:8000
#        forward   .example-isp.net   .
#


forward /	 cache-1.in.crous-toulouse.fr:8080




#
#  5.2. forward-socks4 and forward-socks4a
#  =======================================
#
#  Specifies:
#
#      Through which SOCKS proxy (and to which parent HTTP proxy)
#      specific requests should be routed.
#
#  Type of value:
#
#      target_pattern socks_proxy[:port] http_parent[:port]
#
#      where target_pattern is a URL pattern that specifies to which
#      requests (i.e. URLs) this forward rule shall apply. Use / to
#      denote "all URLs".  http_parent and socks_proxy are IP addresses
#      in dotted decimal notation or valid DNS names (http_parent may
#      be "." to denote "no HTTP forwarding"), and the optional port
#      parameters are TCP ports, i.e. integer values from 1 to 64535
#
#  Default value:
#
#      Unset
#
#  Effect if unset:
#
#      Don't use SOCKS proxies.
#
#  Notes:
#
#      Multiple lines are OK, they are checked in sequence, and the
#      last match wins.
#
#      The difference between forward-socks4 and forward-socks4a
#      is that in the SOCKS 4A protocol, the DNS resolution of the
#      target hostname happens on the SOCKS server, while in SOCKS 4
#      it happens locally.
#
#      If http_parent is ".", then requests are not forwarded to another
#      HTTP proxy but are made (HTTP-wise) directly to the web servers,
#      albeit through a SOCKS proxy.
#
#  Examples:
#
#      From the company example.com, direct connections are made to all
#      "internal" domains, but everything outbound goes through their
#      ISP's proxy by way of example.com's corporate SOCKS 4A gateway
#      to the Internet.
#
#        forward-socks4a   /              socks-gw.example.com:1080   www-cache.example-isp.net:8080
#        forward           .example.com   .
#
#      A rule that uses a SOCKS 4 gateway for all destinations but no
#      HTTP parent looks like this:
#
#        forward-socks4   /               socks-gw.example.com:1080  .
#
#      To chain Privoxy and Tor, both running on the same system,
#      you should use the rule:
#
#        forward-socks4a             /     127.0.0.1:9050 .
#
#      The public Tor network can't be used to reach your local network,
#      therefore it's a good idea to make some exceptions:
#
#        forward         192.168.*.*/     .
#        forward            10.*.*.*/     .
#        forward           127.*.*.*/     .
#
#      Unencrypted connections to systems in these address ranges will
#      be as (un)secure as the local network is, but the alternative is
#      that you can't reach the network at all.
#
#      If you also want to be able to reach servers in your local
#      network by using their names, you will need additional
#      exceptions that look like this:
#
#        forward           localhost/     .
#

#
#  5.3. forwarded-connect-retries
#  ==============================
#
#  Specifies:
#
#      How often Privoxy retries if a forwarded connection request
#      fails.
#
#  Type of value:
#
#      Number of retries.
#
#  Default value:
#
#      0
#
#  Effect if unset:
#
#      Forwarded connections are treated like direct connections and
#      no retry attempts are made.
#
#  Notes:
#
#      forwarded-connect-retries is mainly interesting for socks4a
#      connections, where Privoxy can't detect why the connections
#      failed. The connection might have failed because of a DNS timeout
#      in which case a retry makes sense, but it might also have failed
#      because the server doesn't exist or isn't reachable. In this
#      case the retry will just delay the appearance of Privoxy's
#      error message.
#
#      Only use this option, if you are getting many forwarding related
#      error messages, that go away when you try again manually. Start
#      with a small value and check Privoxy's logfile from time to time,
#      to see how many retries are usually needed.
#
#  Examples:
#
#      forwarded-connect-retries 1
#
forwarded-connect-retries  10

#
#  6. WINDOWS GUI OPTIONS
#  ======================
#
#  Privoxy has a number of options specific to the Windows GUI
#  interface:
#

#  If "activity-animation" is set to 1, the Privoxy icon will animate
#  when "Privoxy" is active. To turn off, set to 0.
#
#activity-animation   1

#  If "log-messages" is set to 1, Privoxy will log messages to the
#  console window:
#
#log-messages   1

#  If "log-buffer-size" is set to 1, the size of the log buffer,
#  i.e. the amount of memory used for the log messages displayed in
#  the console window, will be limited to "log-max-lines" (see below).
#
#  Warning: Setting this to 0 will result in the buffer to grow
#  infinitely and eat up all your memory!
#
#log-buffer-size 1

#  log-max-lines is the maximum number of lines held in the log
#  buffer. See above.
#
#log-max-lines 200

#  If "log-highlight-messages" is set to 1, Privoxy will highlight
#  portions of the log messages with a bold-faced font:
#
#log-highlight-messages 1

#  The font used in the console window:
#
#log-font-name Comic Sans MS

#  Font size used in the console window:
#
#log-font-size 8

#  "show-on-task-bar" controls whether or not Privoxy will appear as
#  a button on the Task bar when minimized:
#
#show-on-task-bar 0

#  If "close-button-minimizes" is set to 1, the Windows close button
#  will minimize Privoxy instead of closing the program (close with
#  the exit option on the File menu).
#
#close-button-minimizes 1

#  The "hide-console" option is specific to the MS-Win console version
#  of Privoxy.  If this option is used, Privoxy will disconnect from
#  and hide the command console.
#
#hide-console

#
```

---

### Post by cfaulkner on 2007-10-22
just use your ISP's SMTP server and save yourself a lot of hassle.

---

### Post by Hasen_A on 2007-10-23
> **cfaulkner said:**
> just use your ISP's SMTP server and save yourself a lot of hassle.

Well first of all I don't know the smtp server address. The admins aren't replying to any emails and secondly I am interested in how TOR and Privoxy work. What's more, I actually got someone from the technical department at the university dorm on the phone this morning and they explained to me that there exists no smtp server for the students and they are blocking all other outgoing connections. At least that's what I understood after asking two times, the french have a really big problem talking slowly to foreigners on the phone :).

---

### Post by scrooge_74 on 2007-10-23
I was checking your privoxy config file, but I cant find this line:

forward-socks4a / localhost:9050 .

it should be at the top in order for tor and privoxy to correctly work, and don't forget the dot at the end of the line

---

### Post by Austin_KW on 2007-10-23
I thought that tor servers blocked port 25, they do not want to be spam central?

---

### Post by Hasen_A on 2007-10-25
> **scrooge_74 said:**
> I was checking your privoxy config file, but I cant find this line:

forward-socks4a / localhost:9050 .

it should be at the top in order for tor and privoxy to correctly work, and don't forget the dot at the end of the line
I assure you it's there. Look again :D.

---

### Post by Hasen_A on 2007-10-25
> **Austin_KW said:**
> I thought that tor servers blocked port 25, they do not want to be spam central?
I have no clue. Well when I go to [http://torcheck.xenobite.eu/]("http://torcheck.xenobite.eu/") to check my connection, it says:

> Your IP is NOT identified to be a Tor-EXIT.
So you are NOT using Tor to reach the web!

---

### Post by scrooge_74 on 2007-10-25
> **Hasen_A said:**
> I have no clue. Well when I go to [http://torcheck.xenobite.eu/]("http://torcheck.xenobite.eu/") to check my connection, it says:

You are right it is there  :lolflag:, but I don't know if it is important, I recall the Howto says to put it at the top of the config file.

Also do you have the tor button install in firefox?

---

### Post by Hasen_A on 2007-10-26
> **scrooge_74 said:**
> You are right it is there  :lolflag:, but I don't know if it is important, I recall the Howto says to put it at the top of the config file.
I dont think this matters, my howto said to put exactly at that line where I have placed it.

> **scrooge_74 said:**
> Also do you have the tor button install in firefox?
Yes I have, but when I activate it, the intranet login for authentication never starts up and HttpsProxyAuthenticator [user_hereneglected]@enseeiht.fr:[password_hereneglected] doesn't seem to do the trick. Firefox returns the following error message:```
The proxy server is refusing connections

Firefox is configured to use a proxy server that is refusing connections.

    *   Check the proxy settings to make sure that they are correct.

    *   Contact your network administrator to make sure the proxy server is working.
```


I know it's a https connection because the site says
```
enter acces by login/password at https://portwifi_chapou.in.crous-toulouse.fr
```

---

