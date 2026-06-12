---
title: "where's the straight forward setup for ipv6?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Xzavier on 2007-06-11
I'm looking for a straight forward walk through for setting up IPV6.

"First this.. Then this.."

All information i come across seems to be in the middle of configuration. no beginning and no end. just discussing the one or 2 complications a user is having.. ](*,)

IF there is any info needed about my setup, ill be happy to post whatcha need!

thanks.

Xz

---

### Post by ramjet_1953 on 2007-06-11
My understaning is that ipv6 is set-up as a standard feature.

Many people want to disable it, though, as it conflicts with ipv5 and slows down Internet performance.

Regards,
Roger :cool:

---

### Post by Xzavier on 2007-06-11
my curiosity for ip6 is the want for vhosts on IRC mostly.. as well its something i want to fully understand i know its still not a set standard so there for there will be alot of conflicts with it. im running and old "book PC" that is mostly used for simple webhosting as well as shells for IRC. but i really would like to implement vhost for custom domains. no more @xx-xxx-xx-xx.state.isp.com

---

### Post by Xzavier on 2007-09-19
to answer my question:

First Sign up for an IPV6 acct, i chose [www.go6.net](www.go6.net)

once that has gone thru, config your tspc.conf
```

#-----------------------------------------------------------------------------
# TSPC.CONF
#-----------------------------------------------------------------------------
#
# THIS SOURCE CODE COPYRIGHT (C) HEXAGO INC. 2002-2004.
#
# THIS PROGRAM IS FREE SOFTWARE; YOU CAN REDISTRIBUTE IT AND/OR MODIFY IT 
# UNDER THE TERMS OF THE GNU GENERAL PUBLIC LICENSE (GPL) VERSION 2, 
# JUNE 1991 AS PUBLISHED BY THE FREE  SOFTWARE FOUNDATION.
#
# THIS PROGRAM IS DISTRIBUTED IN THE HOPE THAT IT WILL BE USEFUL, 
# BUT WITHOUT ANY WARRANTY;  WITHOUT EVEN THE IMPLIED WARRANTY OF 
# MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE.  
# SEE THE GNU GENERAL PUBLIC LICENSE FOR more details.
#
# You should have received a copy of the GNU General Public License 
# along with this program; see the file GPL_LICENSE.txt. If not, write 
# to the Free Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, 
# MA 02111-1307 USA
#------------------------------------------------------------------------------

#
# authentication method:
#  auth_method=any|digest-md5|anonymous|plain
#   any is the prefered one, since the most secure mechanism common to
#    the client and the broker will be used.
#   digest-md5 is sending the username in clear, but no password is sent.
#   plain is sending both username and password in clear.
#   anonymous sends no username and no password
#  recommended: any
auth_method=any

#
# IPv4 address of the client for its tunnel endpoint:
#  client_v4=auto|A.B.C.D (valid ipv4 address)
#  auto = tspc will find the primary ipv4 address
#   on the operating system
#
client_v4=auto

#
# user identification:
#  userid=anonymous|your_userid
#  anonymous means no userid. With anonymous, you don't need to register
#   to get an userid from the broker. However, prefixes (router mode) nor
#   permanent ipv6 address are available in anonymous mode.
#  your_userid means the userid you registered to the broker. The userid
#   must be using only legal dns label names (eg: [a-zA-Z0-9-] ) since
#   the userid is used inside your user hostname.
userid=****

#
# password:
# passwd=your_password
#  leave empty if userid=anonymous
#  your_password means the password you have been assigned with your
#   userid
passwd=****

#
# Name of the script:
# template=checktunnel|setup
#
# the value is the file name of the script in the tsp_dir/template directory
# The script will be executed after the TSP session is completed. The script
#  is configuring the tunnel interface and routes.
# checktunnel is only printing information and does not configure any tunnel
# setup will do the actual work
# you could customize your own script, name it and put the filename in 
#  the template variable.
# on unix, '.sh' is added to the name of the script. 
# on windows, '.bat' is added to the name of the script.
# 
template=setup

#
# 'server' is the tunnel broker identifier
#   Value is the tunnel broker IP address or FQDN and an optional port number
#   The default port number is 3653.
#  
# Examples:
# server=hostname # FQDN
# server=A.B.C.D  # IPv4 address
# server=hostname:port_number  
# server=A.B.C.D:port_number
#
# For users with accounts, 'server' should be set to the Freenet6 
# tunnel broker with authenticated accounts (broker.freenet6.net)
server=broker.freenet6.net
#
# The default value is the Freenet6 tunnel broker for 
# anonymous accounts (anon.freenet6.net)
#server=anon.freenet6.net

# retry_delay=time
# retry tells the client to retry connection after time (seconds) in case of 
# failure or tunnel keepalive timeout (0 = no retry)
retry_delay=30

# Tunnel encapsulation mode:
# tunnel_mode can take the following values
# "v6v4"  request an IPv6 in IPv4 tunnel
# "v6udpv4" request an IPv6 in UDP in IPv4 tunnel (for clients behind a NAT)
# "v6anyv4"   Let the broker choose the tunnel mode appropriate for my client
#  with v6anyv4, the broker will discover if the client is behind a NAT or not
#   and will offer to the TSP client the correct tunnel mode.
# recommended is: v6anyv4
tunnel_mode=v6anyv4

#
# Tunnel Interface name:
# Interface name to use to create the tunnel. This is OS dependent
# and the default is choosen based on the OS. 
# if_tunnel_v6v4 is the tunnel interface name for the v6v4 encapsulation mode
# if_tunnel_v6udpv4 is the tunnel interface name for the v6udpv4 encap mode
if_tunnel_v6v4=sit1
if_tunnel_v6udpv4=tun

#
# proxy_client indicates that this client acts as a TSP proxy for
# some remote client tunnel endpoint machine. Typically, this is set to "yes" if
# we are running this client on a machine that will NOT be configuring
# the tunnel endpoint (for example, using the cisco template).
# This should be used with a static IPv4 address in client_v4 variable.
# NOTE: proxy_client=yes is incompatible with tunnel_mode=v6udpv4
# The default is "no"
proxy_client=no

#
# Keepalive for v6udpv4 tunnels:
#  keepalive indicates that this client will send keepalives to keep the
#   tunnel active (v6udpv4 tunnel) and detect inactive tunnel (no response from
#   server). When a tunnel is determined to be inactive, the TSP client
#   automatically reconnects to the server.
# keepalive_interval is a suggestion from the TSP client to the broker
#  for the interval between two keepalive messages. The broker
#  may impose a different interval value to the client if the interval 
#  value is too low.
# keepalive is "yes" by default
# keepalive_interval is 30 seconds by default
keepalive=yes
keepalive_interval=30

#
# Logging facility uses syslog on Unix platforms
#syslog_facility=DAEMON
#syslog_level=INFO

#
#---------------------
# Router configuration
#
# In order to configure the machine as a router, a prefix must be requested
# and an interface must be specified.  The prefix will be advertised
# through that interface.
#
# host_type=host|router
#  default = host.
host_type=router

#
# prefixlen specifies the required prefix length for the TSP client 
#  network. Valid values are 64 or 48. 64 is for one link. 48 is for
#  a whole enterprise network (65K links).
prefixlen=48

#
# if_prefix is the name of the OS interface that will be configured
#  with the first /64 of the received prefix from the broker and the
#  router advertisement daemon is started to advertise that prefix
#  on the if_prefix interface.
if_prefix=eth0

#
# For reverse DNS delegation of the prefix, define the following:
# Example: dns_server=mydnsserver.domain
dns_server=yourDNSserver.com

# end of tspc.conf
#-----------------------------------------------------------------------------



```

once thats complete run "tspc" as root
if you return to the CL again type ifconfig you should see "tun". thats your tunnel for your ipv6

thats about it! its that simple..

now of course i could be missing a simple step.. but thats all i did after my system rebuild and all is well!
if there are errors please correct me

---

