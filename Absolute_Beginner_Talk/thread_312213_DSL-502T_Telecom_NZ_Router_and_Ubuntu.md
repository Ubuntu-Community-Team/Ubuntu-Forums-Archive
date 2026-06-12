---
title: "DSL-502T Telecom NZ Router and Ubuntu"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by s13_mills on 2006-12-04
Today I was faced with an interesting problem, my family's broadband router (originally a D-Link DSL-302G) gave up the ghost, and we received a new one free of charge from our ISP, XTRA of New Zealand. The new one was a D-Link DSL-502T.

My mother needed to check her emails, so I set up the new router and made sure that the parents' Windows box worked - no problems. I should note that the DSL-502T runs through a Linksys wireless access point before their computer, but the Linksys access point did not cause any problems, so it can go unmentioned. Later in the day when I went to use Firefox on my Dapper system, nothing happened, Firefox opened and attempted to load a page, but it just continued to load it indefinitely, with no result! Synaptic would not work either! Interestingly enough, Konqueror and Limewire worked fine!

A lot of the info I used for fixing my problem came from the thread below, if you have the same issue you may find it helpful too!
[http://ubuntuforums.org/showthread.php?t=225734]("http://ubuntuforums.org/showthread.php?t=225734")

As I say above, I used another thread to find my answers, but I thought it would be appropriate to re-write the directions as specific for XTRA customers who have been given the DSL-502T modem for their ADSL.

To start with, it does no harm to disable ipv6 in Firefox, as ipv6 does not agree with the 502T. In the address bar, type "about:config" then in the "filter:" box type "ipv6". Double-click the only entry there and your Firefox should now work as per normal - mine did.

Next is the issue of Synaptic (or Adept for KDE users) - it still shows no sign of life!

As superuser, modify your /etc/modprobe.d/aliases file with the following:

alias net-pf-10 ipv6 off ##Add this line
alias net-pf-10 off      ##Add this line
alias ipv6 off           ##Add this line
#alias net-pf-10 ipv6    ##Comment out this existing line

Still as superuser, open gedit and create a file called "bad_list" with the contents:

alias net-pf-10 off

Finally as superuser, edit your /etc/modprobe.d/blacklist file, adding:

##Prevent ipv6 from loading
blacklist ipv6

Now reboot your computer. It is interesting to note that in theory, any given ONE of the above three things should work (and may for you), but did not work for me unless I did all 3 at once - I have no idea why!!! Anyone have any ideas?

Upon restarting, go into System>>Administration>>Networking and click on the DNS tab. Get rid of everything written in the DNS servers box and add:

202.27.158.90
202.27.156.72

Next, as superuser, open your /etc/dhcp3/dhclient-script.sh and comment out from:

make_resolv_conf() {
   if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then

to:

        mv -f $new_resolv_conf /etc/resolv.conf
    fi
}

Reboot again, and you should be golden - for me, all services worked fine. Firefox possibly ran a little slower after the second reboot, but maybe it's my imagination. Hope this thread is helpful to people in the same situation as me, maybe you can fix your problems a bit quicker than I did!

---

### Post by whimful on 2006-12-27
thanks for the tips and links man ... really helped ... think synaptic is working now, which is exciting.
i'm brand spanking new here

-john

---

### Post by floydwilde on 2007-01-03
I had the same issue connecting my laptop which runs Debian Etch at my sisters house in Cambridge.   I did mostly what you described and got it mostly working, although still have a bit of weirdness.  Like apt-get update resolving to 1.0.0.0 and not working... sometimes?  I did manage to update about 120 Mbs worth of packages though somehow.   Next time I'm there I'll try to look at it more.

---

### Post by leisuresuitgreg on 2007-04-05
Cheers for the help.

I have one other minor problem tho. I get everything running for about 30 mins, and then the DNS listings change from the one given above back to 10.1.1.1!!! All magically by itself.
Any ideas???

Greg

---

### Post by masked_marsoe on 2007-04-05
I have the same problem, but the DNS only resets to 10.1.1.1 after each reboot. After that I have to reinsert Xtra's DNS.

How can the DNS be locked in?

The other problem is the apt-get always going to 1.0.0.0.
It doesn't matter if it's the nz.ubuntu or other ubuntu sources.

---

