---
title: "ADSL connection at boot"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by justjuice on 2006-10-27
After upgrading to Dapper, my adsl connection does not establish at startup automatically anymore, and I have to manually run pon dsl-provider.  I've tried running pppoeconf again, and it says it will start the connection at boot time, but it doesn't. I've also tried reinstalling pppoe, with no change.  The internet connection is also very flaky, and I have to manually reconnect about once per minute.

Any ideas?

My /etc/network/interfaces file is as below:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

# added by pppoeconf
iface eth0 inet dhcp

    pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

---

### Post by John.Michael.Kane on 2006-10-27
Did you have the same issues before moving to dapper?

If so then it's not pppoeconf. you lines sending you the signal are the issue.

---

### Post by justjuice on 2006-10-27
No, I didn't have this problem before the upgrade.

---

### Post by John.Michael.Kane on 2006-10-27
Have your tried doing a clean install of dapper? downloading iso from your breezy install.

---

### Post by justjuice on 2006-10-29
That's my last resort. Am hoping for something a little easier before I try that.

---

### Post by justjuice on 2006-10-30
Just tried to fix it by upgrading to Edgy.  Now I can't use my computer at all.  Thanks a lot Ubuntu.  Tomorrow I'm going out to buy a copy of Windows.  I'm not wasting any more of my life on this.

---

