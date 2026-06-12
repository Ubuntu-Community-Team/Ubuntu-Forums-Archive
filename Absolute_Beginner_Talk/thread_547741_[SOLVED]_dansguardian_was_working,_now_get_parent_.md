---
title: "[SOLVED] dansguardian was working, now get parent proxy error"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by keymoo on 2007-09-10
Hi there,

I installed DansGuardian using apt-get with tinyproxy and firehol and it worked fine. I have now rebooted my Ubuntu Server (no GUI) and when I try to start DansGuardian I get this error;

```
Error connecting to parent proxy
```

tinyproxy is running and I tried restarting it, firehol and DansGuardian but I still get the error.

tinyproxy.conf:
```
##
## tinyproxy.conf -- tinyproxy daemon configuration file
##

#
# Name of the user the tinyproxy daemon should switch to after the port
# has been bound.
#
User root
Group root

#
# Port to listen on.
#
Port 3128

#
# If you have multiple interfaces this allows you to bind to only one. If
# this is commented out, tinyproxy will bind to all interfaces present.
#
Listen 192.168.0.6

#
# The Bind directive allows you to bind the outgoing connections to a
# particular IP address.
#
#Bind 192.168.0.1

#
# Timeout: The number of seconds of inactivity a connection is allowed to
# have before it closed by tinyproxy.
#
Timeout 600

#
# ErrorFile: Defines the HTML file to send when a given HTTP error
# occurs.  You will probably need to customize the location to your
# particular install.  The usual locations to check are:
#   /usr/local/share/tinyproxy
#   /usr/share/tinyproxy
#   /etc/tinyproxy
#
# ErrorFile 404 "/usr/share/tinyproxy/404.html"
# ErrorFile 400 "/usr/share/tinyproxy/400.html"
# ErrorFile 503 "/usr/share/tinyproxy/503.html"
# ErrorFile 403 "/usr/share/tinyproxy/403.html"
# ErrorFile 408 "/usr/share/tinyproxy/408.html"

# 
# DefaultErrorFile: The HTML file that gets sent if there is no
# HTML file defined with an ErrorFile keyword for the HTTP error
# that has occured.
#
DefaultErrorFile "/usr/share/tinyproxy/default.html"

#
# StatFile: The HTML file that gets sent when a request is made
# for the stathost.  If this file doesn't exist a basic page is
# hardcoded in tinyproxy.
#
StatFile "/usr/share/tinyproxy/stats.html"

#
# Where to log the information. Either LogFile or Syslog should be set,
# but not both.
#
Logfile "/var/log/tinyproxy.log"
# Syslog On

#
# Set the logging level. Allowed settings are:
#    Critical    (least verbose)
#    Error
#    Warning
#    Notice
#    Connect        (to log connections without Info's noise)
#    Info        (most verbose)
# The LogLevel logs from the set level and above. For example, if the LogLevel
# was set to Warning, than all log messages from Warning to Critical would be
# output, but Notice and below would be suppressed.
#
LogLevel Info

#
# PidFile: Write the PID of the main tinyproxy thread to this file so it
# can be used for signalling purposes.
#
PidFile "/var/run/tinyproxy.pid"

#
# Include the X-Tinyproxy header, which has the client's IP address when
# connecting to the sites listed.
#
#XTinyproxy mydomain.com

#
# Turns on upstream proxy support.
#
# The upstream rules allow you to selectively route upstream connections
# based on the host/domain of the site being accessed.
#
# For example:
#  # connection to test domain goes through testproxy
#  upstream testproxy:8008 ".test.domain.invalid"
#  upstream testproxy:8008 ".our_testbed.example.com"
#  upstream testproxy:8008 "192.168.128.0/255.255.254.0"
#
#  # no upstream proxy for internal websites and unqualified hosts
#  no upstream ".internal.example.com"
#  no upstream "www.example.com"
#  no upstream "10.0.0.0/8"
#  no upstream "192.168.0.0/255.255.254.0"
#  no upstream "."
#
#  # connection to these boxes go through their DMZ firewalls
#  upstream cust1_firewall:8008 "testbed_for_cust1"
#  upstream cust2_firewall:8008 "testbed_for_cust2"
#
#  # default upstream is internet firewall
#  upstream firewall.internal.example.com:80
#
# The LAST matching rule wins the route decision.  As you can see, you
# can use a host, or a domain:
#  name     matches host exactly
#  .name    matches any host in domain "name"
#  .        matches any host with no domain (in 'empty' domain)
#  IP/bits  matches network/mask
#  IP/mask  matches network/mask
#
#Upstream some.remote.proxy:port

#
# This is the absolute highest number of threads which will be created. In
# other words, only MaxClients number of clients can be connected at the
# same time.
#
MaxClients 100

#
# These settings set the upper and lower limit for the number of
# spare servers which should be available. If the number of spare servers
# falls below MinSpareServers then new ones will be created. If the number
# of servers exceeds MaxSpareServers then the extras will be killed off.
#
MinSpareServers 5
MaxSpareServers 20

#
# Number of servers to start initially.
#
StartServers 10

#
# MaxRequestsPerChild is the number of connections a thread will handle
# before it is killed. In practise this should be set to 0, which disables
# thread reaping. If you do notice problems with memory leakage, then set
# this to something like 10000
#
MaxRequestsPerChild 0

#
# The following is the authorization controls. If there are any access
# control keywords then the default action is to DENY. Otherwise, the
# default action is ALLOW.
#
# Also the order of the controls are important. The incoming connections
# are tested against the controls based on order.
#
Allow 127.0.0.1
Allow 192.168.0.0/24

#
# The "Via" header is required by the HTTP RFC, but using the real host name
# is a security concern.  If the following directive is enabled, the string
# supplied will be used as the host name in the Via header; otherwise, the
# server's host name will be used.
#
ViaProxyName "tinyproxy"

#
# The location of the filter file.
#
Filter "/etc/tinyproxy/filter"

#
# Filter based on URLs rather than domains.
#
FilterURLs On

#
# Use POSIX Extended regular expressions rather than basic.
#
#FilterExtended On

#
# Use case sensitive regular expressions.
#                                                                         
#FilterCaseSensitive On     

#
# Change the default policy of the filtering system.  If this directive is
# commented out, or is set to "No" then the default policy is to allow
# everything which is not specifically denied by the filter file.
#
# However, by setting this directive to "Yes" the default policy becomes to
# deny everything which is _not_ specifically allowed by the filter file.
#
#FilterDefaultDeny Yes

#
# If an Anonymous keyword is present, then anonymous proxying is enabled.
# The headers listed are allowed through, while all others are denied. If
# no Anonymous keyword is present, then all header are allowed through.
# You must include quotes around the headers.
#
#Anonymous "Host"
#Anonymous "Authorization"

#
# This is a list of ports allowed by tinyproxy when the CONNECT method
# is used.  To disable the CONNECT method altogether, set the value to 0.
# If no ConnectPort line is found, all ports are allowed (which is not
# very secure.)
#
# The following two ports are used by SSL.
#
ConnectPort 443
ConnectPort 563
```dansguardian.conf
```
# DansGuardian config file for version 2.8.0 with Anti-Virus plug-in 6.4.3
# **NOTE** as of version 2.7.5 most of the list files are now in dansguardianf1.conf
#UNCONFIGURED - Please remove this line after configuration


# Web Access Denied Reporting (does not affect logging)
#
# -1 = log, but do not block - Stealth mode
#  0 = just say 'Access Denied'
#  1 = report why but not what denied phrase
#  2 = report fully
#  3 = use HTML template file (accessdeniedaddress ignored) - recommended
#
reportinglevel = 3

# Language dir where languages are stored for internationalisation.
# The HTML template within this dir is only used when reportinglevel
# is set to 3. When used, DansGuardian will display the HTML file instead of
# using the perl cgi script.  This option is faster, cleaner
# and easier to customise the access denied page.
# The language file is used no matter what setting however.
#
languagedir = '/etc/dansguardian/languages'

# language to use from languagedir.
language = 'ukenglish'

# Logging Settings
#
# 0 = none  1 = just denied  2 = all text based  3 = all requests
# DG   default: 2
# DGAV default: 3
loglevel = 3

# Log Exception Hits
# Log if an exception (user, ip, URL, phrase) is matched and so
# the page gets let through.  Can be useful for diagnosing
# why a site gets through the filter.  on | off
logexceptionhits = on

# Log File Format
# 1 = DansGuardian format        2 = CSV-style format
# 3 = Squid Log File Format      4 = Tab delimited
logfileformat = 1


# Log file location
# 
# Defines the log directory and filename.
#loglocation = '/var/log/dansguardian/access.log'


# Network Settings
# 
# the IP that DansGuardian listens on.  If left blank DansGuardian will
# listen on all IPs.  That would include all NICs, loopback, modem, etc.
# Normally you would have your firewall protecting this, but if you want
# you can limit it to only 1 IP.  Yes only one.
filterip =

# the port that DansGuardian listens to.
filterport = 8080

# the ip of the proxy (default is the loopback - i.e. this server)
proxyip = 127.0.0.1

# the port DansGuardian connects to proxy on
proxyport = 3128

# accessdeniedaddress is the address of your web server to which the cgi
# dansguardian reporting script was copied
# Do NOT change from the default if you are not using the cgi.
#
accessdeniedaddress = 'http://YOURSERVER.YOURDOMAIN/cgi-bin/dansguardian.pl'

# Non standard delimiter (only used with accessdeniedaddress)
# Default is enabled but to go back to the original standard mode dissable it.
nonstandarddelimiter = on



# Banned image replacement
# Images that are banned due to domain/url/etc reasons including those
# in the adverts blacklists can be replaced by an image.  This will,
# for example, hide images from advert sites and remove broken image
# icons from banned domains.
# 0 = off
# 1 = on (default)
usecustombannedimage = 1
custombannedimagefile = '/etc/dansguardian/transparent1x1.gif'



# Filter groups options
# filtergroups sets the number of filter groups. A filter group is a set of content
# filtering options you can apply to a group of users.  The value must be 1 or more.
# DansGuardian will automatically look for dansguardianfN.conf where N is the filter
# group.  To assign users to groups use the filtergroupslist option.  All users default
# to filter group 1.  You must have some sort of authentication to be able to map users
# to a group.  The more filter groups the more copies of the lists will be in RAM so
# use as few as possible.
filtergroups = 1
filtergroupslist = '/etc/dansguardian/filtergroupslist'



# Authentication files location
bannediplist = '/etc/dansguardian/bannediplist'
exceptioniplist = '/etc/dansguardian/exceptioniplist'
banneduserlist = '/etc/dansguardian/banneduserlist'
exceptionuserlist = '/etc/dansguardian/exceptionuserlist'



# Show weighted phrases found
# If enabled then the phrases found that made up the total which excedes
# the naughtyness limit will be logged and, if the reporting level is
# high enough, reported. on | off
showweightedfound = on

# Weighted phrase mode
# There are 3 possible modes of operation:
# 0 = off = do not use the weighted phrase feature.
# 1 = on, normal = normal weighted phrase operation.
# 2 = on, singular = each weighted phrase found only counts once on a page.
#
weightedphrasemode = 2



# Positive result caching for text URLs
# Caches good pages so they don't need to be scanned again
# 0 = off (recommended for ISPs with users with disimilar browsing)
# 1000 = recommended for most users (DG)
# 3000 = recommended when urlcacheonly is on (DGAV)
# 5000 = suggested max upper limit
urlcachenumber = 3000
#
# Age before they are stale and should be ignored in seconds
# 0 = never
# 900 = recommended = 15 mins
urlcacheage = 900



# Smart and Raw phrase content filtering options
# Smart is where the multiple spaces and HTML are removed before phrase filtering
# Raw is where the raw HTML including meta tags are phrase filtered
# CPU usage can be effectively halved by using setting 0 or 1
# 0 = raw only
# 1 = smart only
# 2 = both (default)
phrasefiltermode = 2



# Lower casing options
# When a document is scanned the uppercase letters are converted to lower case
# in order to compare them with the phrases.  However this can break Big5 and
# other 16-bit texts.  If needed preserve the case.  As of version 2.7.0 accented
# characters are supported.
# 0 = force lower case (default)
# 1 = do not change case
preservecase = 0



# Hex decoding options
# When a document is scanned it can optionally convert %XX to chars.
# If you find documents are getting past the phrase filtering due to encoding
# then enable.  However this can break Big5 and other 16-bit texts.
# 0 = disabled (default)
# 1 = enabled
hexdecodecontent = 0



# Force Quick Search rather than DFA search algorithm
# The current DFA implementation is not totally 16-bit character compatible
# but is used by default as it handles large phrase lists much faster.
# If you wish to use a large number of 16-bit character phrases then
# enable this option.
# 0 = off (default)
# 1 = on (Big5 compatible)
forcequicksearch = 0



# Reverse lookups for banned site and URLs.
# If set to on, DansGuardian will look up the forward DNS for an IP URL
# address and search for both in the banned site and URL lists.  This would
# prevent a user from simply entering the IP for a banned address.
# It will reduce searching speed somewhat so unless you have a local caching
# DNS server, leave it off and use the Blanket IP Block option in the
# bannedsitelist file instead.
reverseaddresslookups = off



# Reverse lookups for banned and exception IP lists.
# If set to on, DansGuardian will look up the forward DNS for the IP
# of the connecting computer.  This means you can put in hostnames in
# the exceptioniplist and bannediplist.
# It will reduce searching speed somewhat so unless you have a local DNS server, 
# leave it off.
reverseclientiplookups = off



# Build bannedsitelist and bannedurllist cache files.
# This will compare the date stamp of the list file with the date stamp of
# the cache file and will recreate as needed.
# If a bsl or bul .processed file exists, then that will be used instead.
# It will increase process start speed by 300%.  On slow computers this will
# be significant.  Fast computers do not need this option. on | off
createlistcachefiles = on



# POST protection (web upload and forms)
# does not block forms without any file upload, i.e. this is just for
# blocking or limiting uploads
# measured in kibibytes after MIME encoding and header bumph
# use 0 for a complete block
# use higher (e.g. 512 = 512Kbytes) for limiting
# use -1 for no blocking
#maxuploadsize = 512
#maxuploadsize = 0
maxuploadsize = -1



# Max content filter page size
# Sometimes web servers label binary files as text which can be very
# large which causes a huge drain on memory and cpu resources.
# To counter this, you can limit the size of the document to be
# filtered and get it to just pass it straight through.
# This setting also applies to content regular expression modification.
# The size is in Kibibytes - eg 2048 = 2Mb
# use 0 for no limit
maxcontentfiltersize = 256



# Username identification methods (used in logging)
# You can have as many methods as you want and not just one.  The first one
# will be used then if no username is found, the next will be used.
# * proxyauth is for when basic proxy authentication is used (no good for
#   transparent proxying).
# * ntlm is for when the proxy supports the MS NTLM authentication
#   protocol.  (Only works with IE5.5 sp1 and later).  **NOT IMPLEMENTED**
# * ident is for when the others don't work.  It will contact the computer
#   that the connection came from and try to connect to an identd server
#   and query it for the user owner of the connection.
usernameidmethodproxyauth = on
usernameidmethodntlm = off # **NOT IMPLEMENTED**
usernameidmethodident = off



# Preemptive banning - this means that if you have proxy auth enabled and a user accesses
# a site banned by URL for example they will be denied straight away without a request
# for their user and pass.  This has the effect of requiring the user to visit a clean
# site first before it knows who they are and thus maybe an admin user.
# This is how DansGuardian has always worked but in some situations it is less than
# ideal.  So you can optionally disable it.  Default is on.
# As a side effect disabling this makes AD image replacement work better as the mime
# type is know.
preemptivebanning = on



# Misc settings

# if on it adds an X-Forwarded-For: <clientip> to the HTTP request
# header.  This may help solve some problem sites that need to know the
# source ip. on | off
forwardedfor = off


# if on it uses the X-Forwarded-For: <clientip> to determine the client
# IP. This is for when you have squid between the clients and DansGuardian.
# Warning - headers are easily spoofed. on | off
usexforwardedfor = off


# if on it logs some debug info regarding fork()ing and accept()ing which
# can usually be ignored.  These are logged by syslog.  It is safe to leave
# it on or off
logconnectionhandlingerrors = on



# Fork pool options

# sets the maximum number of processes to sporn to handle the incomming
# connections.  Max value usually 250 depending on OS.
# On large sites you might want to try 180.
maxchildren = 120


# sets the minimum number of processes to sporn to handle the incomming connections.
# On large sites you might want to try 32.
minchildren = 8


# sets the minimum number of processes to be kept ready to handle connections.
# On large sites you might want to try 8.
minsparechildren = 4


# sets the minimum number of processes to sporn when it runs out
# On large sites you might want to try 10.
preforkchildren = 6


# sets the maximum number of processes to have doing nothing.
# When this many are spare it will cull some of them.
# On large sites you might want to try 64.
maxsparechildren = 32


# sets the maximum age of a child process before it croaks it.
# This is the number of connections they handle before exiting.
# On large sites you might want to try 10000.
maxagechildren = 500



# Process options
# (Change these only if you really know what you are doing).
# These options allow you to run multiple instances of DansGuardian on a single machine.
# Remember to edit the log file path above also if that is your intention.

# IPC filename
# 
# Defines IPC server directory and filename used to communicate with the log process.
ipcfilename = '/tmp/.dguardianipc'

# URL list IPC filename
# 
# Defines URL list IPC server directory and filename used to communicate with the URL
# cache process.
urlipcfilename = '/tmp/.dguardianurlipc'

# PID filename
# 
# Defines process id directory and filename.
#pidfilename = '/var/run/dansguardian.pid'

# Disable daemoning
# If enabled the process will not fork into the background.
# It is not usually advantageous to do this.
# on|off ( defaults to off )
nodaemon = off

# Disable logging process
# on|off ( defaults to off )
nologger = off

# Daemon runas user and group
# This is the user that DansGuardian runs as.  Normally the user/group nobody.
# Uncomment to use.  Defaults to the user set at compile time.
# daemonuser = 'nobody'
# daemongroup = 'nobody'

# Soft restart
# When on this disables the forced killing off all processes in the process group.
# This is not to be confused with the -g run time option - they are not related.
# on|off ( defaults to off )
softrestart = off



# ANTIVIRUS SETTINGS
# --------------------

# OPTION: virusscan
# If on, we scan all downloaded content using embedded virus engine.
# Supported engines of this version are ClamAV, ClamDScan, KAV, KAV5, Trophie, Sophie.
# If off, we don't scan any downloaded content.
# See http://sourceforge.net/projects/dgav/ for more details.
virusscan = off

# OPTION: virusengine
# Set the embedded virus scan engine to be used (clamav, clamdscan, kav, aveserver, trophie, sophie).
virusengine = 'clamav'

# OPTION: tricklelength
# With tricklelength you can choose between three different trickle modes:
# a) If set to -1, the scanner will send 1 byte per delay period
#    to the client to keep a download connection alive.
#    When the whole file is downloaded and scanned, the client will
#    receive all remaining bytes, if the file was clean.
# b) If set to less than -1 (eg. -1024) the scanner will send,
#    after firsttrickledelay seconds, a proportional amount of data
#    to the client (e.g 1024 bytes per downloaded megabyte); after
#    followingtrickledelay seconds again a proportional amount
#    of data is sent to the client and so on. When the whole file is
#    downloaded and scanned, the client will receive all remaining
#    bytes, if the file was clean.
#    Recommended value: -1024 (1024 bytes per downloaded megabyte)
# c) If set to a positive integer value it enables immediate delivery
#    to the client. The value set means minimum number of bytes of the
#    downloaded file that will be held and delivered after virus scan.
#    If clean, the remaining bytes will be sent to the client.
#    If infected, file downloaded will be incomplete and a warning message 
#    will be sent to the postmaster and possibly the user.
#    Recommended minimum positive value: 32768 (32 kbytes)
#
# NOTE:
#    only trickle modes a) and b) allow for limited mime-header
#    rewriting; eg. if a zip file (application/zip) is downloaded
#    and contains a virus it's mime-type is rewritten to text/html
#    which in turn forces the browser to display the warning page;
#    be aware however, that this is only possible for downloads
#    that finish within firsttrickledelay seconds!
tricklelength = 32768

# OPTION: forkscanlength
# Specifies maximum file size, in bytes, that is scanned w/o parallel trickling.
# Files larger than 'forkscan_length' will be scanned in the background,
# while a foreground process trickles data to the client in order to keep
# connection alive.
# This heavily depends on the available CPU speed. Slow CPUs need smaller values.
# The size is in Kibibytes - eg 2048 = 2Mb
forkscanlength = 32768

# OPTION: firsttrickledelay
# Delay in seconds to deliver the first byte to the client.
# This option only applies if tricklelength is set to -1.
firsttrickledelay = 10

# OPTION: follwingtrickledelay
# Delay in seconds to deliver subsequent bytes to the client.
# This option only applies if tricklelength is set to -1.
followingtrickledelay = 10

# OPTION: maxcontentscansize
# Set the maximum size of a content to be virus scanned.
# Content size above this value will not be scanned against viruses.
# The size is in Kibibytes - eg 2048 = 2Mb
# To have no limit, use 0 (zero).
maxcontentscansize = 41904304

# OPTION: virusscanexceptions
# If off, antivirus scanner will ignore DG exception sites and urls.
virusscanexceptions = on

# OPTION: urlcachecleanonly
# If off, url cache will contain entries of text only urls.
# Keeping it off, preserves original Dansguardian feature and
# downloaded content will be always scanned by antivirus.
# When turned on, urlcache will be loaded only with content
# found to be good and that is virus free.
# Thus, content of urls found in urlcache WILL NOT BE SCANNED AGAIN.
urlcachecleanonly = on

# OPTION: virusscannertimeout
# The maximum length of time the commercial virus scanner is allowed to run
# for 1 batch of messages (in seconds).
virusscannertimeout = 60

# OPTION: notify
# Sets who receives email notification when a virus is found.
# Users must be authenticated to be able to receive messages.
# Email address for users will be formed by the authentication name received by DG
# plus @emaildomain (see option below)
# 0 = disabled
# 1 = user only
# 2 = postmaster only
# 3 = postmaster and users (default)
notify = 0

# OPTION: emaildomain
# Set email domain to use when notifying users of an infected file.
# This is just the domain name part, after the @
emaildomain = 'your.domain.com'

# OPTION: postmaster
# Set email address of who to notify about any infections found.
# Should put your full domain name here too.
postmaster = 'postmaster@your.domain.com'

# OPTION: emailserver
# Set the address and port of the Mail Server to send notifications through.
#
emailserver = '127.0.0.1:25'


# OPTION: downloaddir
# Set where the files are downloaded to before they are scanned.
# Since version 6.4.2 it is strongly recommended to define a directory path
# TO BE USED ONLY BY DGAV.
# YOU WILL LOOSE FILES inside this directory path if it is used for any other purpose.
downloaddir = '/tmp/dgvirus'

# CLAMAV SETTINGS
# --------------------
# OPTION: clmaxfiles
# Set maximum number of files inside a compressed file
# default: 1500 files
clmaxfiles = 1500

# OPTION: clmaxreclevel
# Set maximum recursion level to perform scan on a compressed file
# that is inside a compressed file
# default: 3 levels
clmaxreclevel = 3

# OPTION: clmaxfilesize
# Set maximum file size of a file inside a compressed file
# default: 10485760 = 10 Mbytes
clmaxfilesize = 10485760

# OPTION: clblockencryptedarchives
# Treat encrypted compressed file as virus infected content.
# default: off
clblockencryptedarchives = off


# OPTION: cldetectbroken
# Activate improved detection of broken executable files.
# default: off
cldetectbroken = off


# CLAMDSCAN SETTINGS
# --------------------
# OPTION: clamdsocket
# Set the name of a local clamd socket (file)
# or the hostname:port of a remote clamd server
# default: '/tmp/clamd'
clamdsocket = '/tmp/clamd'


# KASPERSKY 5 SETTINGS
# --------------------
# OPTION: avesocket
# Set name of the local socket file
# default: '/var/run/aveserver'
avesocket = '/var/run/aveserver'


# TROPHIE SETTINGS
# --------------------
# OPTION: trophiesocket
# Set name of the local socket file
# default: '/var/run/trophie'
trophiesocket = '/var/run/trophie'


# SOPHIE SETTINGS
# --------------------
# OPTION: sophiesocket
# Set name of the local socket file
# default: '/var/run/sophie'
sophiesocket = '/var/run/sophie'


# ICAP SETTINGS (experimental)
# ----------------------------
# OPTION: icapsocket
# Set hostname:port of the icap server
# default: 'localhost:1344'
icapsocket = 'localhost:1344'

# OPTION: icapservice
# Set the icap service to be used
# default: 'icap://localhost/avscan'
icapservice = 'icap://localhost/avscan'
```firehol.conf
```
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

#
# Added from:
# http://ubuntuforums.org/showthread.php?t=207008
#

iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept
#server webcache accept

#
####
#

version 5

# Accept all client traffic on any interface
interface any world
    client all accept

```Any ideas on how to fix the problem?

Thanks.

---

### Post by keymoo on 2007-09-11
ok, this is what I did to get it all working

```
sudo apt-get --purge autoremove --assume-yes "dansguardian"
sudo apt-get --purge autoremove --assume-yes "tinyproxy"
sudo apt-get --purge autoremove --assume-yes "firehol"
```

Rebooted the server

I then installed squid, configured it for my needs, then installed DansGuardian and all is well! Feels good as I'm new to linux and I managed to solve my first problem all on my own (well with a bit of help from my old friend, the internet)

:)

---

