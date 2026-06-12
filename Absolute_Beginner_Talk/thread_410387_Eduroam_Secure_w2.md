---
title: "Eduroam Secure w2?"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by mech7 on 2007-04-15
On my school they use Securew2 program on XP sp2 to connect to eduroam to have internet connection.. but how can i connect to this on ubuntu? They only give support for xp 0_o

[http://www.securew2.com/](http://www.securew2.com/)

This is the manuel in dutch.. [http://www.hva.nl/documenten/eduroam-handleiding-lan-wlan.pdf](http://www.hva.nl/documenten/eduroam-handleiding-lan-wlan.pdf)

---

### Post by mech7 on 2007-04-16
:( nobody?

---

### Post by pgilmon on 2007-05-24
On Feisty, just create the file /etc/wpa_supplicant.conf, edit it so that it looks like:

```
ctrl_interface=/var/run/wpa_supplicant
        eapol_version=1
        ap_scan=1
        fast_reauth=1
        network={
                ssid="eduroam"
                scan_ssid=1
                key_mgmt=WPA-EAP
                proto=WPA
                eap=TTLS
                identity="XXX@XXX.xx"       # <- just like user in SecureW2
                password="xxxxxx"              # <- password you use for SecureW2
                priority=2
                phase2="auth=PAP"
                }
```

Make sure all interfaces are down. and type:

```
sudo wpa_supplicant -i eth1 -D wext -c /etc/wpa_supplicant.conf
```

When it says it's connected, open another terminal and type:

```
sudo dhclient eth1
```

And you're done

Of course, if your wi-fi interface is other than eth1, you should use it instead of eth1. It might be also possible that your wi-fi card doens't work with the wext driver. In that case, I don't know exactly what you should do (use other driver instead of wext?).

Note that I find it difficult sometimes to connect after being connected to another network. and I have to play a bit with System->Administration->Network to make sure that eth1 is down, but eventually, it will connect.

---

### Post by hugomeeuwes on 2007-11-02
For Erasmus University Rotterdam this would be the code for wpa_supplicant.conf:
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=0

network={
key_mgmt=IEEE8021X
eap=TTLS
identity="000000aa@eur.nl" #change to your erna login
anonymous_identity ="000000aa@eur.nl"
password="pass"
phase2="auth=PAP"
}

```
note that I am using wpa_supplicant on a wired connection. ap_scan is zero because I don't need to look for hotspots.

to use this script add
 pre-up wpa_supplicant -Bw -Dwired -ieth0 -c/etc/wpa_supplicant.conf
 pre-down killall -q wpa_supplicant -c/etc/wpa_supplicant.conf
to your interfaces file:

```
auto eth0
iface eth0 inet dhcp
pre-up wpa_supplicant -Bw -Dwired -ieth0 -c/etc/wpa_supplicant.conf
pre-down killall -q wpa_supplicant
```

Once again, because my connection is wired, it say's -Dwired, otherwise it would be -Dwext
Make sure that the location of wpa_supplicant.conf in the interfaces file is equal to the actual location.
And for the real noobs: eth0 should be changed to your outgoing network card.

now restart your connection (or reboot) and it will work.
if your securew2 uses certificates, add them to the wpa_supplicant.conf too. Just google to see how that works. It's really simple.

---

### Post by mech7 on 2007-11-06
hmm this did not work.. how can i make sure the interfaces are down ?

> **pgilmon said:**
> On Feisty, just create the file /etc/wpa_supplicant.conf, edit it so that it looks like:

```
ctrl_interface=/var/run/wpa_supplicant
        eapol_version=1
        ap_scan=1
        fast_reauth=1
        network={
                ssid="eduroam"
                scan_ssid=1
                key_mgmt=WPA-EAP
                proto=WPA
                eap=TTLS
                identity="XXX@XXX.xx"       # <- just like user in SecureW2
                password="xxxxxx"              # <- password you use for SecureW2
                priority=2
                phase2="auth=PAP"
                }
```

Make sure all interfaces are down. and type:

```
sudo wpa_supplicant -i eth1 -D wext -c /etc/wpa_supplicant.conf
```

When it says it's connected, open another terminal and type:

```
sudo dhclient eth1
```

And you're done

Of course, if your wi-fi interface is other than eth1, you should use it instead of eth1. It might be also possible that your wi-fi card doens't work with the wext driver. In that case, I don't know exactly what you should do (use other driver instead of wext?).

Note that I find it difficult sometimes to connect after being connected to another network. and I have to play a bit with System->Administration->Network to make sure that eth1 is down, but eventually, it will connect.

---

### Post by viciouslime on 2007-11-28
You could try using the deb file I have produced for students at The University of York, it looks like it should work for you too. In fact I think it should work for any University connected to Janet...

You can get it from the downloads section of my site ([http://www.viciouslime.co.uk]("http://www.viciouslime.co.uk"))

---

### Post by jobr on 2007-12-14
[http://docs.google.com/Doc?docid=dfmq2m4v_128g3m3bjf5&hl=en](http://docs.google.com/Doc?docid=dfmq2m4v_128g3m3bjf5&hl=en)

Its Danish, but you will get the point, download the secureW2.zip, extract the certificate, and then fill out the connection manager as described.

---

### Post by Marsch123 on 2008-01-07
I am also living in a students appartment in Rotterdam and wanted to use some time that I have here to get familiar with the Ubuntu basics. I spent the entire afternoon to get Internet access, but I didn't make it. I am a student at Hogeschool Rotterdam, not at Erasmus University, but I am pretty sure that they use the same system. I created the file wpa_supplicant.conf in the /etc folder and inserted this script:
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=0

network = {
key_mgmt=IEEE8021X
eap=TTLS
identity="0796534@hro.nl"
anonymous_identity ="0796534@hro.nl"
password="xxxxx"
phase2="auth=PAP"
}
```

Than I edited the /etc/network/interfaces file like this:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up wpa_supplicant -Bw -Dwired -ieth0 -c/etc/wpa_supplicant.conf
pre-down killall -q wpa_supplicant

```
Now I get Access to the Kenninglas website, where I can download the SecureW2 Client for Windows, which doesn't help me in this case.  Nontheless. a step forward but not INternet yet. You guys wrote that it might be necessary to add some kind of certificate. I am not sure whether this is relevant in my case and unfortunately I don't have more information on the underlying system (just a step by step manual how to do it with this client and Windows, which doesn't help me in this case).
Could you please take a look at my configuration and write me your opinion.
Thank you very much in advance!

---

### Post by harrydb on 2008-02-26
See my post in this thread for a howto connecting to eduroam using the network manager applet:
[http://ubuntuforums.org/showthread.php?t=708148#post4410798](http://ubuntuforums.org/showthread.php?t=708148#post4410798)

---

