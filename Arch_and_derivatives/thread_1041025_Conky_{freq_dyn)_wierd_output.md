---
title: "Conky {freq_dyn) wierd output"
date: 2009-01-16
forum: Arch and derivatives
---

### Post by SnakeHips on 2009-01-16
Hi ,I'm getting a wierd output using the {freq_dyn} variable (see screenshot)

Arch64
AMD64

I should add the variable is reported correctly on my Hardy64 setup ,same conkyrc...

any ideas?

/.conkyrc <snip>
```

TEXT

${voffset -1} Kernel: ${color e0e0e0}${font}${kernel}${color} | ${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} | ${color e0e0e0}${**freq_dyn**}Mhz ${color}${font} | CPU: ${color e0e0e0}${font}${cpu}% ${color} | RAM: ${color e0e0e0}${font}${mem} ${color} | Nvidia ${execi 30 nvclock -i | grep 'Card:' | cut -c16-29}${color e0e0e0}${font} ${execi 30 nvidia-settings -q gpucoretemp |grep '):' | awk '{print $4}'}C ${color} | ${color}${time %a %e %B %G}  | ${color e0e0e0}${font}${time %H:%M} |${color e0e0e0} ${if_running mpd}${color}${font}${mpd_smart | fold -w20} - ${color 004151}$mpd_album ${color}$endif | 

```

/etc/rc.conf <snip>
```

# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng iptables network netfs crond alsa mpd sensors hal fam **cpufreq** )	

MOD_AUTOLOAD="yes"
#MOD_BLACKLIST=() #deprecated
MODULES=(**powernow-k8 cpufreq_ondemand** skge slhc ac97_bus snd-mixer-oss snd-pcm-oss snd-seq-oss snd-seq-device snd-seq-midi-event snd-seq snd-page-alloc snd-pcm snd-rawmidi snd-timer snd snd-mpu401-uart snd-ac97-codec snd-via82xx-modem snd-via82xx soundcore fuse)

```

/etc/conf.d/cpufreq
```

#configuration for cpufreq control

# valid governors:
#  ondemand, performance, powersave,
#  conservative, userspace
governor="**ondemand**"

# valid suffixes: Hz, kHz (default), MHz, GHz, THz
#min_freq="2.25GHz"
#max_freq="3GHz"

```

edit: my hunch is it's displaying the value in 'hz' instead of 'Mhz'

---

### Post by fwojciec on 2009-01-16
Does this bug report help?  (see also the comments, reason for closing)
[http://sourceforge.net/tracker/index.php?func=detail&aid=2431615&group_id=143975&atid=757308]("http://sourceforge.net/tracker/index.php?func=detail&aid=2431615&group_id=143975&atid=757308")
What is special about ${freq_dyn} variable?  I just use ${freq_g} and it works well.

---

### Post by SnakeHips on 2009-01-16
Doh ,trust me not to version check!
Arch  conky 1.6.1.2
Hardy conky 1.5.1.1

..and I appreciate you taking the time to help with this - thankyou. 
It would have saved me some time if the Dev had updated here :-(
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

"What is special about ${freq_dyn} variable? I just use ${freq_g} and it works well."
It just shows the actual freq the cpu is running at rather than the flat-out figure you see when using {freq} or {freq_g}. On Hardy it seems to range anywhere between 800Mhz and 2100Mhz.....just wondered if i'd setup Arch differently. Anyway the upshot is I can remove two modules from rc.conf now *I think* so that may be a result :-)

cheers

---

