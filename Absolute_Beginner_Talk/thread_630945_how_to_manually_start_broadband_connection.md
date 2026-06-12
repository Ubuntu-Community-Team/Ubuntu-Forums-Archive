---
title: "how to manually start broadband connection"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by emnaki on 2007-12-03
Right now to manually start my broadband connection, I have to run 'sudo pppoeconf', ok to all the options, type in my username and password...etc. Is there an easier way to do it?

---

### Post by Severun on 2007-12-03
You can create a configuration file in /etc/ppp/peers

I have one called verizon

That looks something like

> ttyUSB0
115200
debug
noauth
defaultroute
usepeerdns
connect-delay 20000
user [email]xxxxxxxxxx@vzw3g.com[/email]
show-password
crtscts
lock
lcp-echo-failure 4
connect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/verizon_chat'
disconnect '/usr/sbin/chat -v -t3 -f /etc/ppp/peers/verizon_disc'

My 

verizon_chat looks like

> TIMEOUT 20
ABORT 'BUSY'
ABORT 'NO ANSWER'
ABORT 'NO CARRIER'
SAY 'Starting Verizon\'
'' 'AT'
'OK' 'ATQ0V1E0'
'OK' 'ATZ'
'OK' 'AT&F'
SAY 'Connecting'
'OK' 'ATDT#777'
CONNECT CLIENT

my verizon_disc is:

> "" "\K"
"" "+++ATH0"
SAY "Disconnected from Verizon."



Then at the prompt I just type:

> sudo pppd call verizon

You can to a:

> tail -f /var/log/messages

If you want to see the connection debugging output

This works with the Kyocera KPC6650 broadband card and Verizon in the US.  Just replace xxxxxxxxxx with your area code and phone number.

and it does the rest

Hope that helps ya..

---

