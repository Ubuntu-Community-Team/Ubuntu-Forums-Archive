---
title: "[SOLVED] Hardy sound problems on TiBook"
date: 2008-08-31
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2008-08-31
In my never ending quest to make sound work tried kernel2.6.24-19-smp with no luck. It's worse than the non-smp version.
As I have posted elsewhere I had sound perfectly until updating the kernel as requested by Update Manager. Now I have system sounds sometimes but that's it.
When starting 2.6.24-19-powerpc I went into text mode and saw an error similar to:
"modprobe FATAL: error inserting snd_sequence_dummy  see dmesg"

So I checked dmesg and get this regarding snd:
```
[   35.760893] snd_seq_midi: disagrees about version of symbol snd_seq_kernel_client_dispatch
[   35.760907] snd_seq_midi: Unknown symbol snd_seq_kernel_client_dispatch
[   35.760977] snd_seq_midi: disagrees about version of symbol snd_midi_event_encode
[   35.760982] snd_seq_midi: Unknown symbol snd_midi_event_encode
[   35.761121] snd_seq_midi: disagrees about version of symbol snd_seq_dump_var_event
[   35.761126] snd_seq_midi: Unknown symbol snd_seq_dump_var_event
[   35.761838] snd_seq_midi: disagrees about version of symbol snd_midi_event_decode
[   35.761843] snd_seq_midi: Unknown symbol snd_midi_event_decode
[   35.770310] snd_seq_midi: disagrees about version of symbol snd_seq_kernel_client_dispatch
[   35.770321] snd_seq_midi: Unknown symbol snd_seq_kernel_client_dispatch
[   35.770389] snd_seq_midi: disagrees about version of symbol snd_midi_event_encode
[   35.770394] snd_seq_midi: Unknown symbol snd_midi_event_encode
[   35.770533] snd_seq_midi: disagrees about version of symbol snd_seq_dump_var_event
[   35.770538] snd_seq_midi: Unknown symbol snd_seq_dump_var_event
[   35.771250] snd_seq_midi: disagrees about version of symbol snd_midi_event_decode
[   35.771255] snd_seq_midi: Unknown symbol snd_midi_event_decode
[   36.472089] eth1: Hardware identity 0005:0001:0001:0002
[   36.472212] eth1: Station identity  001f:0001:0008:0046
[   36.472218] eth1: Firmware determined as Lucent/Agere 8.70
[   36.472222] eth1: Ad-hoc demo mode supported
[   36.472230] eth1: IEEE standard IBSS ad-hoc mode supported
[   36.472234] eth1: WEP supported, 104-bit key
[   36.472307] eth1: MAC address 00:30:65:25:8d:87
[   36.472389] eth1: Station name "HERMES I"
[   36.472933] eth1: ready
[   36.478881] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   36.478988] ttyPZ0 at MMIO 0x80013020 (irq = 22) is a Z85c30 ESCC - Serial port
[   36.479713] ttyPZ1 at MMIO 0x80013000 (irq = 23) is a Z85c30 ESCC - Serial port
[   36.633374] airport: Card registered for interface eth1
[   36.930278] snd_seq_dummy: disagrees about version of symbol snd_seq_kernel_client_dispatch
[   36.930292] snd_seq_dummy: Unknown symbol snd_seq_kernel_client_dispatch
[   37.449603] snd_aoa_i2sbus: disagrees about version of symbol snd_pcm_new
[   37.449616] snd_aoa_i2sbus: Unknown symbol snd_pcm_new
[   37.449749] snd_aoa_i2sbus: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   37.449754] snd_aoa_i2sbus: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   37.450030] snd_aoa_i2sbus: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   37.450035] snd_aoa_i2sbus: Unknown symbol snd_pcm_lib_malloc_pages
[   37.450103] snd_aoa_i2sbus: disagrees about version of symbol snd_pcm_lib_ioctl
[   37.450108] snd_aoa_i2sbus: Unknown symbol snd_pcm_lib_ioctl
[   37.450261] snd_aoa_i2sbus: disagrees about version of symbol snd_pcm_lib_free_pages
[   37.450266] snd_aoa_i2sbus: Unknown symbol snd_pcm_lib_free_pages
[   37.450414] snd_aoa_i2sbus: disagrees about version of symbol snd_pcm_new_stream
[   37.450419] snd_aoa_i2sbus: Unknown symbol snd_pcm_new_stream
[   37.450509] snd_aoa_i2sbus: disagrees about version of symbol snd_pcm_set_ops
[   37.450514] snd_aoa_i2sbus: Unknown symbol snd_pcm_set_ops
[   37.450744] snd_aoa_i2sbus: disagrees about version of symbol snd_pcm_suspend_all
[   37.450749] snd_aoa_i2sbus: Unknown symbol snd_pcm_suspend_all
[   37.451050] snd_aoa_i2sbus: disagrees about version of symbol snd_pcm_period_elapsed
[   37.451055] snd_aoa_i2sbus: Unknown symbol snd_pcm_period_elapsed

```

Any ideas?

Many thanks!!

---

### Post by ubuntubrian on 2008-08-31
So right now sound has returned-go figure! I suspended my laptop and upon waking the touchpad was working but no sound. I decided to check volume control-all OK. I checked alsamixer, strangely only the master channel appeared though in volume control I have many channels.
I checked pulseaudio and it reported "connection refused".
I went back into sound preferences and checked enable esd. Pulse then connected and I tested sound in preferences and all the tests created sound that didn't cut out, though it popped a bit.
The final test was an .ogg file on my desktop that played fine.
My ~/.asoundrc file is intact.
So it seems as if things are back tonormal-sort of. I noticed this after I first upgraded to Hardy. It's as if the software settles in and starts working better.
BTW, in all my other efforts pulseaudio was connected, esd enabled, .asoundrc in place, etc. Go figure!
Oh, I did this too, building and installing new alsamodules, and maybe it was the fix?
[http://ubuntuforums.org/showthread.php?t=738275](http://ubuntuforums.org/showthread.php?t=738275)

---

