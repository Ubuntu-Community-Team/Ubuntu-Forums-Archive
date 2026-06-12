---
title: "JACK settings under Lubuntu 13.04"
date: 2013-06-09
forum: Any Other OS
---

### Post by Brendo613 on 2013-06-09
Under AV linux I was able to record through a firewire mixer using JACK and Audacity. I did this for 2+ years, but AV linux is no longer supported and had too many bugs. Running Lubuntu 13.04, I can only get settings that - best - incur one xrun every 30 minutes. Through much unguided tinkering of JACK's settings, this is the best I could get. Under AV linux I had no xruns. Reliable performance is a must!

Below is the latest JACK messages window output. Attached are current JACK settings.

```
Jack: jack_client_open qjackctl
Jack: JackLibGlobals Init 0
Jack: JackLibGlobals
Jack: JackPosixThread::StartImp : create non RT thread
Jack: JackPosixThread::ThreadHandler : start
Jack: JackGenericClientChannel::ServerCheck = default
Jack: JackClientSocket::Connect : addr.sun_path /dev/shm/jack_default_1000_0
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
Jack: JackClientSocket::Close
jack server is not running or cannot be started
Jack: JackLibGlobals Destroy 952fca0
Jack: ~JackLibGlobals
Jack: no message buffer overruns
Jack: JackPosixThread::Stop
Jack: JackPosixThread::ThreadHandler : exit
12:29:13.561 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
12:29:13.640 JACK connection change.
12:29:13.644 Server configuration saved to "/home/acer/.jackdrc".
12:29:13.647 Statistics reset.
12:29:13.660 Client activated.
12:29:13.667 JACK connection graph change.
Jack: jack_client_open qjackctl
Jack: JackLibGlobals Init 0
Jack: JackLibGlobals
Jack: JackPosixThread::StartImp : create non RT thread
Jack: JackPosixThread::ThreadHandler : start
Jack: JackGenericClientChannel::ServerCheck = default
Jack: JackClientSocket::Connect : addr.sun_path /dev/shm/jack_default_1000_0
Jack: JackClientSocket::Close
Jack: JackLibClient::JackLibClient table = 952fcbc
Jack: JackLibClient::Open name = qjackctl
Jack: JackSocketClientChannel::Open name = qjackctl
Jack: JackClientSocket::Connect : addr.sun_path /dev/shm/jack_default_1000_0
Jack: JackServerSocket::Bind : addr.sun_path /dev/shm/jack_qjackctl_1000_0
Jack: JackSocketClientChannel::Start
Jack: JackPosixThread::StartImp : create non RT thread
Jack: JackPosixThread::ThreadHandler : start
Jack: JackSocketClientChannel::Init
Jack: JackServerSocket::Close /dev/shm/jack_qjackctl_1000_0
Jack: JackClient::ClientNotify ref = 0 name = system notify = 0
Jack: JackClient::AddClient name = system, ref = 0 
Jack: JackPosixSemaphore::Connect name = jack_sem.1000_default_system
Jack: JackPosixSemaphore::Connect sem_getvalue 0
Jack: JackClient::ClientNotify ref = 1 name = freewheel notify = 0
Jack: JackClient::AddClient name = freewheel, ref = 1 
Jack: JackPosixSemaphore::Connect name = jack_sem.1000_default_freewheel
Jack: JackPosixSemaphore::Connect sem_getvalue 0
Jack: JackClient::ClientNotify ref = 2 name = dbusapi notify = 0
Jack: JackClient::AddClient name = dbusapi, ref = 2 
Jack: JackPosixSemaphore::Connect name = jack_sem.1000_default_dbusapi
Jack: JackPosixSemaphore::Connect sem_getvalue 0
Jack: JackShmReadWritePtr::Init 1 -1
Jack: Succeeded in locking 994 byte memory area
Jack: JackShmReadWritePtr::Init 0 -1
Jack: Succeeded in locking 82274202 byte memory area
Jack: JackShmReadWritePtr1::Init 2 -1
Jack: Succeeded in locking 422 byte memory area
Sun Jun  9 12:29:13 2013: Saving settings to "/home/acer/.config/jack/conf.xml" ...
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in'
Sun Jun  9 12:29:13 2013: New client 'firewire_pcm' with PID 0
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 1+2 right_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 3+4 left_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 3+4 right_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 5+6 left_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 5+6 right_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 7+8 left_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 7+8 right_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifIn left_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifIn right_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_MidiIn_in'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 3+4 left_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 3+4 right_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 5+6 left_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 5+6 right_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 7+8 left_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 7+8 right_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifOut left_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifOut right_out'
Sun Jun  9 12:29:13 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_MidiOut_out'
Sun Jun  9 12:29:13 2013: New client 'qjackctl' with PID 1802
12:29:19.727 JACK connection graph change.
Sun Jun  9 12:29:19 2013: New client 'PortAudio' with PID 2237
12:29:20.407 JACK connection graph change.
12:29:24.489 XRUN callback (1).
12:29:30.308 JACK connection graph change.
12:29:30.329 JACK connection change.
12:29:30.375 JACK connection graph change.
Sun Jun  9 12:29:30 2013: Connecting 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in' to 'PortAudio:in_1'
Sun Jun  9 12:29:30 2013: Connecting 'PortAudio:out_0' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:29:30 2013: Connecting 'PortAudio:out_1' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
12:29:31.315 Statistics reset.
12:31:08.633 XRUN callback (1).
12:31:20.783 XRUN callback (2).
12:31:25.027 JACK connection graph change.
12:31:25.103 JACK connection change.
Sun Jun  9 12:31:25 2013: Disconnecting 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in' from 'PortAudio:in_1'
Sun Jun  9 12:31:25 2013: Disconnecting 'PortAudio:out_0' from 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:31:25 2013: Disconnecting 'PortAudio:out_1' from 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
12:31:29.341 JACK connection graph change.
12:31:29.519 JACK connection change.
Sun Jun  9 12:31:29 2013: Connecting 'PortAudio:out_2' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:31:29 2013: Connecting 'PortAudio:out_3' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
12:31:53.925 JACK connection graph change.
12:31:53.969 JACK connection change.
Sun Jun  9 12:31:53 2013: Disconnecting 'PortAudio:out_2' from 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:31:53 2013: Disconnecting 'PortAudio:out_3' from 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
12:32:15.067 Client deactivated.
12:32:21.210 D-BUS: JACK server is stopping...
Sun Jun  9 12:32:03 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Sun Jun  9 12:32:03 2013: [1m[31mERROR: JackEngine::ClientDeactivate wait error ref = 4 name = PortAudio[0m
Sun Jun  9 12:32:04 2013: [1m[31mERROR: JackFFADODriver::ffado_driver_wait - unhandled xrun[0m
Sun Jun  9 12:32:04 2013: [1m[31mERROR: firewire ERR: wait status < 0! (= -1)[0m
Sun Jun  9 12:32:04 2013: [1m[31mERROR: JackAudioDriver::ProcessAsync: read error, stopping...[0m
Sun Jun  9 12:32:08 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Sun Jun  9 12:32:08 2013: [1m[31mERROR: JackEngine::ClientDeactivate wait error ref = 3 name = qjackctl[0m
Sun Jun  9 12:32:13 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Sun Jun  9 12:32:13 2013: [1m[31mERROR: JackEngine::ClientDeactivate wait error ref = 4 name = PortAudio[0m
Sun Jun  9 12:32:13 2013: [1m[31mERROR: JackEngine::ClientKill ref = 4 cannot be removed from the graph !![0m
Sun Jun  9 12:32:14 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 1000000 err = Connection timed out[0m
Sun Jun  9 12:32:14 2013: [1m[31mERROR: JackEngine::ClientCloseAux wait error ref = 4[0m
Sun Jun  9 12:32:14 2013: Client 'PortAudio' with PID 2237 is out
Sun Jun  9 12:32:15 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 1000000 err = Connection timed out[0m
Sun Jun  9 12:32:15 2013: [1m[31mERROR: JackEngine::ClientCloseAux wait error ref = 3[0m
Sun Jun  9 12:32:15 2013: Client 'qjackctl' with PID 1802 is out
Sun Jun  9 12:32:15 2013: Stopping jack server...
Sun Jun  9 12:32:20 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Sun Jun  9 12:32:20 2013: [1m[31mERROR: JackEngine::ClientDeactivate wait error ref = 2 name = dbusapi[0m
Sun Jun  9 12:32:20 2013: [1m[31mERROR: failed to deactivate dbusapi jack client. error is -1[0m
Sun Jun  9 12:32:20 2013: Client 'firewire_pcm' with PID 0 is out
12:32:21.276 D-BUS: JACK server was stopped (org.jackaudio.service aka jackdbus).
Sun Jun  9 12:32:21 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 1000000 err = Connection timed out[0m
Sun Jun  9 12:32:21 2013: [1m[31mERROR: JackEngine::ClientCloseAux wait error ref = 2[0m
12:32:41.464 D-BUS: JACK server is starting...
Sun Jun  9 12:32:38 2013: Starting jack server...
Sun Jun  9 12:32:39 2013: JACK server starting in realtime mode with priority 80
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
12:32:41.554 JACK connection change.
12:32:41.557 Server configuration saved to "/home/acer/.jackdrc".
12:32:41.560 Statistics reset.
12:32:41.580 Client activated.
12:32:41.621 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
12:32:41.627 JACK connection graph change.
Sun Jun  9 12:32:41 2013: Saving settings to "/home/acer/.config/jack/conf.xml" ...
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in'
Sun Jun  9 12:32:41 2013: New client 'firewire_pcm' with PID 0
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 1+2 right_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 3+4 left_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 3+4 right_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 5+6 left_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 5+6 right_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 7+8 left_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 7+8 right_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifIn left_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifIn right_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_MidiIn_in'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 3+4 left_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 3+4 right_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 5+6 left_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 5+6 right_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 7+8 left_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 7+8 right_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifOut left_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifOut right_out'
Sun Jun  9 12:32:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_MidiOut_out'
Sun Jun  9 12:32:41 2013: New client 'qjackctl' with PID 1802
12:32:49.887 JACK connection graph change.
Sun Jun  9 12:32:49 2013: New client 'PortAudio' with PID 2272
12:32:50.419 JACK connection graph change.
12:32:50.473 JACK connection change.
12:32:50.497 JACK connection graph change.
12:32:50.679 JACK connection change.
12:32:53.676 XRUN callback (1).
12:33:01.513 XRUN callback (2).
12:33:04.928 JACK connection graph change.
12:33:05.116 JACK connection change.
Sun Jun  9 12:33:05 2013: Connecting 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in' to 'PortAudio:in_2'
Sun Jun  9 12:33:05 2013: Connecting 'PortAudio:out_1' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:33:05 2013: Connecting 'PortAudio:out_2' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
Sun Jun  9 12:33:12 2013: [1m[31mERROR: JackFFADODriver::ffado_driver_wait - unhandled xrun[0m
Sun Jun  9 12:33:12 2013: [1m[31mERROR: firewire ERR: wait status < 0! (= -1)[0m
Sun Jun  9 12:33:12 2013: [1m[31mERROR: JackAudioDriver::ProcessAsync: read error, stopping...[0m
12:33:15.951 JACK connection graph change.
Sun Jun  9 12:33:15 2013: Disconnecting 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in' from 'PortAudio:in_2'
Sun Jun  9 12:33:15 2013: Disconnecting 'PortAudio:out_1' from 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:33:15 2013: Disconnecting 'PortAudio:out_2' from 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
12:33:20.951 JACK connection graph change.
Sun Jun  9 12:33:20 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Sun Jun  9 12:33:20 2013: [1m[31mERROR: JackEngine::ClientDeactivate wait error ref = 4 name = PortAudio[0m
Sun Jun  9 12:33:20 2013: [1m[31mERROR: JackEngine::ClientKill ref = 4 cannot be removed from the graph !![0m
Sun Jun  9 12:33:20 2013: [1m[31mERROR: Failed to find port 'PortAudio:in_2' to destroy[0m
Sun Jun  9 12:33:20 2013: [1m[31mERROR: Failed to find port 'PortAudio:out_1' to destroy[0m
Sun Jun  9 12:33:20 2013: [1m[31mERROR: Failed to find port 'PortAudio:out_2' to destroy[0m
12:33:21.345 JACK connection change.
Sun Jun  9 12:33:21 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 1000000 err = Connection timed out[0m
Sun Jun  9 12:33:21 2013: [1m[31mERROR: JackEngine::ClientCloseAux wait error ref = 4[0m
Sun Jun  9 12:33:21 2013: Client 'PortAudio' with PID 2272 is out
12:33:29.875 Client deactivated.
12:33:35.975 D-BUS: JACK server is stopping...
Sun Jun  9 12:33:28 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Sun Jun  9 12:33:28 2013: [1m[31mERROR: JackEngine::ClientDeactivate wait error ref = 3 name = qjackctl[0m
Sun Jun  9 12:33:29 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 1000000 err = Connection timed out[0m
Sun Jun  9 12:33:29 2013: [1m[31mERROR: JackEngine::ClientCloseAux wait error ref = 3[0m
Sun Jun  9 12:33:29 2013: Client 'qjackctl' with PID 1802 is out
Sun Jun  9 12:33:29 2013: Stopping jack server...
Sun Jun  9 12:33:34 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out[0m
Sun Jun  9 12:33:34 2013: [1m[31mERROR: JackEngine::ClientDeactivate wait error ref = 2 name = dbusapi[0m
Sun Jun  9 12:33:34 2013: [1m[31mERROR: failed to deactivate dbusapi jack client. error is -1[0m
Sun Jun  9 12:33:34 2013: Client 'firewire_pcm' with PID 0 is out
Sun Jun  9 12:33:35 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 1000000 err = Connection timed out[0m
Sun Jun  9 12:33:35 2013: [1m[31mERROR: JackEngine::ClientCloseAux wait error ref = 2[0m
12:33:36.020 D-BUS: JACK server was stopped (org.jackaudio.service aka jackdbus).
12:34:24.451 D-BUS: JACK server is starting...
Sun Jun  9 12:34:21 2013: Starting jack server...
Sun Jun  9 12:34:22 2013: JACK server starting in realtime mode with priority 80
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
12:34:24.541 JACK connection change.
12:34:24.545 Server configuration saved to "/home/acer/.jackdrc".
12:34:24.547 Statistics reset.
12:34:24.557 Client activated.
12:34:24.571 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
12:34:24.576 JACK connection graph change.
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in'
Sun Jun  9 12:34:24 2013: New client 'firewire_pcm' with PID 0
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 1+2 right_in'
Sun Jun  9 12:34:24 2013: Saving settings to "/home/acer/.config/jack/conf.xml" ...
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 3+4 left_in'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 3+4 right_in'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 5+6 left_in'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 5+6 right_in'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 7+8 left_in'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 7+8 right_in'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifIn left_in'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifIn right_in'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_MidiIn_in'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 3+4 left_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 3+4 right_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 5+6 left_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 5+6 right_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 7+8 left_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 7+8 right_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifOut left_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifOut right_out'
Sun Jun  9 12:34:24 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_MidiOut_out'
Sun Jun  9 12:34:24 2013: New client 'qjackctl' with PID 1802
12:34:42.670 JACK connection graph change.
Sun Jun  9 12:34:42 2013: New client 'PortAudio' with PID 2473
12:34:43.196 JACK connection graph change.
12:34:43.204 JACK connection change.
12:34:43.221 JACK connection graph change.
12:34:43.414 JACK connection change.
12:34:49.363 XRUN callback (1).
12:34:52.795 JACK connection graph change.
12:34:52.846 JACK connection change.
12:34:52.863 JACK connection graph change.
Sun Jun  9 12:34:52 2013: Connecting 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in' to 'PortAudio:in_2'
Sun Jun  9 12:34:52 2013: Connecting 'PortAudio:out_1' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:34:52 2013: Connecting 'PortAudio:out_2' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
12:34:59.770 XRUN callback (2).
12:35:03.277 JACK connection graph change.
12:35:03.473 JACK connection change.
Sun Jun  9 12:35:03 2013: Disconnecting 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in' from 'PortAudio:in_2'
Sun Jun  9 12:35:03 2013: Disconnecting 'PortAudio:out_1' from 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:35:03 2013: Disconnecting 'PortAudio:out_2' from 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
12:35:05.013 JACK connection graph change.
12:35:05.087 JACK connection change.
Sun Jun  9 12:35:05 2013: Connecting 'PortAudio:out_3' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 12:35:05 2013: Connecting 'PortAudio:out_4' to 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
Sun Jun  9 12:35:10 2013: [1m[31mERROR: JackFFADODriver::ffado_driver_wait - unhandled xrun[0m
Sun Jun  9 12:35:10 2013: [1m[31mERROR: firewire ERR: wait status < 0! (= -1)[0m
Sun Jun  9 12:35:10 2013: [1m[31mERROR: JackAudioDriver::ProcessAsync: read error, stopping...[0m
12:35:38.752 Client deactivated.
12:35:50.957 D-BUS: JACK server is stopping...
Sun Jun  9 12:35:36 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 10000000 err = Connection timed out[0m
Sun Jun  9 12:35:36 2013: [1m[31mERROR: JackEngine::ClientDeactivate wait error ref = 3 name = qjackctl[0m
Sun Jun  9 12:35:38 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 2000000 err = Connection timed out[0m
Sun Jun  9 12:35:38 2013: [1m[31mERROR: JackEngine::ClientCloseAux wait error ref = 3[0m
Sun Jun  9 12:35:38 2013: Client 'qjackctl' with PID 1802 is out
Sun Jun  9 12:35:38 2013: Stopping jack server...
Sun Jun  9 12:35:48 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 10000000 err = Connection timed out[0m
Sun Jun  9 12:35:48 2013: [1m[31mERROR: JackEngine::ClientDeactivate wait error ref = 2 name = dbusapi[0m
Sun Jun  9 12:35:48 2013: [1m[31mERROR: failed to deactivate dbusapi jack client. error is -1[0m
Sun Jun  9 12:35:48 2013: Client 'firewire_pcm' with PID 0 is out
Sun Jun  9 12:35:48 2013: Client 'PortAudio' with PID 2473 is out
12:35:51.013 D-BUS: JACK server was stopped (org.jackaudio.service aka jackdbus).
Sun Jun  9 12:35:50 2013: [1m[31mERROR: JackPosixProcessSync::LockedTimedWait error usec = 2000000 err = Connection timed out[0m
Sun Jun  9 12:35:50 2013: [1m[31mERROR: JackEngine::ClientCloseAux wait error ref = 2[0m
```

This version of Lubuntu also lags sometimes while opening programs ... never had that problem before. Unfortunately I'm really in the dark with what next steps to take. There's too much about JACK I don't know! Portaudio, xrun, buffer, frames ... I want to use a Debian-based, LXDE-based distribution to record on but do I need a degree?

---

### Post by Brendo613 on 2013-06-09
Tinkered more, then followed the instructions on [how to ensure JACK is using realtime scheduling.]("http://jackaudio.org/linux_rt_config") JACK appears to operate correctly (no realtime error message, etc.) but I still incur xruns. Curiously, running JACK and Audacity as root seems to yield a usable recording setup ... at least there's a stopgap glimmer of hope!

---

### Post by Brendo613 on 2013-06-09
The beacon of hope has extinguished. Recording as root does *not* yield xrun-free results. The test run that appeared to yield xrun-free results was a new audio project. When I attempted to add tracks on a previous recording, the xruns returned. After 3:45 of recording, Audacity froze up all together. This has been happening after the past few days of attempted JACK optimization. After Audacity crashes, I need to manually kill Audacity, jackdbus, qjackctl, and qjackctl.real in task manager. Currently I'm running a 3.8.0.22 low-latency kernel as installed through synaptic.

---

### Post by Brendo613 on 2013-06-09
Running new JACK settings now. This is from the messages window output:

```
17:55:41.570 D-BUS: JACK server is starting...
Sun Jun  9 17:55:38 2013: Starting jack server...
Sun Jun  9 17:55:38 2013: JACK server starting in realtime mode with priority 89
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
17:55:41.612 D-BUS: JACK server was started (org.jackaudio.service aka jackdbus).
Sun Jun  9 17:55:41 2013: Saving settings to "/home/acer/.config/jack/conf.xml" ...
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 1+2 left_in'
Sun Jun  9 17:55:41 2013: New client 'firewire_pcm' with PID 0
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 1+2 right_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 3+4 left_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 3+4 right_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 5+6 left_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 5+6 right_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 7+8 left_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineIn 7+8 right_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifIn left_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifIn right_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_MidiIn_in'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 1+2 left_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 1+2 right_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 3+4 left_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 3+4 right_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 5+6 left_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 5+6 right_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 7+8 left_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_LineOut 7+8 right_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifOut left_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_SpdifOut right_out'
Sun Jun  9 17:55:41 2013: graph reorder: new port 'firewire_pcm:000a9200c6020929_MidiOut_out'
17:55:42.900 JACK connection change.
17:55:42.904 Server configuration saved to "/home/acer/.jackdrc".
17:55:42.906 Statistics reset.
17:55:42.917 Client activated.
17:55:42.950 JACK connection graph change.
Sun Jun  9 17:55:42 2013: New client 'qjackctl' with PID 3718
17:58:23.597 Client deactivated.
17:58:24.163 D-BUS: JACK server is stopping...
Sun Jun  9 17:58:23 2013: Client 'qjackctl' with PID 3718 is out
Sun Jun  9 17:58:23 2013: Stopping jack server...
Sun Jun  9 17:58:23 2013: Client 'firewire_pcm' with PID 0 is out
17:58:24.176 D-BUS: JACK server was stopped (org.jackaudio.service aka jackdbus).
```

What do the "cannot connect to server" errors mean? This is the only part of the output that looks problematic to me.

---

