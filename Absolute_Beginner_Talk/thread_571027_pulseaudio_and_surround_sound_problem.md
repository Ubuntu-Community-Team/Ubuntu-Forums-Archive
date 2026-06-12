---
title: "pulseaudio and surround sound problem"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by koga85 on 2007-10-08
Hi everyone!

I'm fairly new in Ubuntu and I've just run into a problem. I have a Terratec 5.1 soundcard, installed pulseaudio sound server which works fine with all the applications I tried but the problem is that surround speakers won't work perfectly only the front speakers. Before the pulseaudio installation my modified .asoundrc file worked fine for upmixing stereo channels to 5.1. After my rear speakers are quiet. In the pulseaudio manager the server default sample type is set to s16le 2ch 44100Hz. Is there any workaround to solve this problem?

Thanks for your replies in advance.

Here is my asoundrc file:

pcm.!default {
        type pulse
        slave.pcm "surround51"
        slave.channels 6
        route_policy duplicate
}

pcm.!spdif {
    type pulse
    slave.pcm "dmix"
}

pcm.analog {
    type pulse
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

---

