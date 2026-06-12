---
title: "Very slow internet connection"
date: 2004-10-14
forum: Apple PPC Users
---

### Post by germanoob on 2004-10-14
Now that my monitor issue is solved with the help of the Ubuntu-community here's the next main prob: 
Connecting to the internet with Firefox is poorly slow, what to do?
I do have a fast adsl-connection via my Vigor-router and Ubuntu is the only OS where this problem appears. Can someone give me detailed advice, where i have to look, which file i have to modify to solve this issue?

Greetings

Dieter

Edit: This seems to be a more general issue. After searching in the forums i tried this hint:
 [http://ubuntuforums.org/viewtopic.php?t=189](http://ubuntuforums.org/viewtopic.php?t=189)
but nothing changed at all
what makes me think that this is a more general prob is the fact, that for example at booting Ubuntu the startup process is paused for about one minute or so, when the system is trying to synchronise with the time server.
this minute is about the same time it lasts to open a website in Firefox or to connext to the mailserver in Evolution.
Like i said before: i am connected to the www via vigor router which is configured as dhcp server.
maybe this has something to do with the domain name server entry?
My  ISP (t-online Germany) doesn't recommend to make a DNS-entry because they change this server from time to time and they say that i am automaticly connected to the idle one...

---

### Post by germanoob on 2004-10-15
To whom it may concern: it was indeed this DNS thing. Added 3 alternative t-online DNS numbers in network-admin and now Firefox runs as hell  :twisted:  :D -

---

### Post by python on 2005-01-17
[QUOTE=germanoob]To whom it may concern: it was indeed this DNS thing. Added 3 alternative t-online DNS numbers in network-admin and now Firefox runs as hell  :twisted:  :D -[/QUOTE]
 Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

nameserver 212.74.112.66
nameserver 212.74.112.67

Your ISPs nameservers replacing mine ;-P
Nameserver 192.168.blah.blah should either be commented out (preceded with a #) or not be there at all.



Finally, go to /etc/dhcp3/dhclient-script and comment out this:

# Modified for Debian. Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# if [ -n "$new_domain_name" ]; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}


That should have you sorted sunshine!

---

### Post by matthewhaworth on 2008-06-26
How do you go about finding your ISPs nameservers?

---

### Post by stream303 on 2008-06-26
Just call them, or see if they have online documenation.

However, if you don't know them, you can use some alternates.  Many favor OpenDNS servers. See the bottom-right of their page:

[http://www.opendns.com/](http://www.opendns.com/)

I could just print them here, but it is best to verify them for yourself.

If you are behind a router, I like to place these addresses into the router's setup page, rather than define them on each machine.  In many cases this can solve some dns headaches.

---

