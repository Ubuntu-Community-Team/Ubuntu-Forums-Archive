---
title: "jack pulse-audio firewire"
date: 2012-03-22
forum: Any Other OS
---

### Post by uPilger on 2012-03-22
Hi,
I try Dream Studio. For the first, it's a great idea.
My problem is the preconfigured jack-pulse-audio.
I'll use a external firewire. It works with ubuntu 11.10 out of the box.
But in Dream Studio 11.04 and 11.10 jack will not start.
Here is the jack-log. It seems that jack find the firewire, but what is the reason for not starting? I'm looking for /etc/asound.conf or $HOME/.asoundrc to check the config. But these files are not present.
Thanks for help.
```
10:17:20.333 Steckfeld deaktiviert.
10:17:20.334 Statistik zurückgesetzt.
10:17:20.354 ALSA-Verbindung geändert.
10:17:20.383 JACK-Verbindung geändert.
10:17:20.396 Client aktiviert
10:17:29.844 Schaubild der JACK-Verbindungen geändert.
10:17:29.886 Schaubild der ALSA-Verbindungen geändert.
10:17:36.685 Schaubild der JACK-Verbindungen geändert.
10:17:36.724 Schaubild der ALSA-Verbindungen geändert.
10:27:02.827 Client deaktiviert.
10:27:02.828 Nach-Herunterfahr-Skript...
10:27:02.828 pulsejackdisconnect
10:27:07.542 Nach-Herunterfahr-Skript beendet erfolgreich.
10:27:16.192 Start-Skript...
10:27:16.193 killall pulseaudio
Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden
Cannot connect to server socket
jack server is not running or cannot be started
10:27:16.597 Start-Skript beendet erfolgreich.
10:27:16.597 JACK startet...
10:27:16.597 /usr/bin/jackd -n(voreinst.) -v -dfirewire -d/dev/audio -r44100 -p512 -n3
10:27:16.599 JACK wurde mit PID = 3710 gestartet.
no message buffer overruns
10:27:16.640 Keine Verbindungsaufnahme als Client zum JACK-Server möglich. - Gesamtbetrieb schlug fehl. - Verbindungsaufnahme zum Server gescheitert. Bitte sehen Sie im Meldungsfenster nach weiteren Informationen.
Cannot connect to server socket err = Datei oder Verzeichnis nicht gefunden
Cannot connect to server socket
jack server is not running or cannot be started
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackDriver::Open capture_driver_name = 
Jack: JackDriver::Open playback_driver_name = 
Jack: Check protocol client 8 server = 8
Jack: JackEngine::ClientInternalOpen: name = system
Jack: JackEngine::AllocateRefNum ref = 0
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_(voreinst.)_system val = 0
Jack: JackEngine::NotifyAddClient: name = system
Jack: JackGraphManager::SetBufferSize size = 512
Jack: JackConnectionManager::DirectConnect first: ref1 = 0 ref2 = 0
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 0 ref2 = 0
Jack: JackDriver::SetupDriverSync driver sem in flush mode
Jack: JackSocketServerChannel::Open
Jack: Bind: addr.sun_path /dev/shm/jack_(voreinst.)_1000_0
Jack: JackSocketServerChannel::BuildPoolTable size = 1
Jack: JackEngine::Open
Jack: Connect: addr.sun_path /dev/shm/jack_(voreinst.)_1000_0
Jack: JackEngine::ClientInternalOpen: name = freewheel
Jack: JackEngine::AllocateRefNum ref = 1
Jack: JackPosixSemaphore::Allocate name = jack_sem.1000_(voreinst.)_freewheel val = 0
Jack: JackEngine::NotifyAddClient: name = freewheel
Jack: JackConnectionManager::DirectConnect first: ref1 = 1 ref2 = 1
Jack: JackGraphManager::ConnectRefNum cur_index = 0 ref1 = 1 ref2 = 1
Jack: JackDriver::SetupDriverSync driver sem in flush mode
Jack: JackFFADODriver::Attach fBufferSize 512 fSampleRate 44100
libffado 2.999.0- built Oct 12 2011 22:59:42
firewire MSG: Streaming thread running with Realtime scheduling, priority 15
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 1+2 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 1 name = firewire_pcm:00000ff200031248_LineIn 1+2 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 1
Jack: JackFFADODriver::Attach fCapturePortList[i] 1 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 1+2 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 2 name = firewire_pcm:00000ff200031248_LineIn 1+2 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 2
Jack: JackFFADODriver::Attach fCapturePortList[i] 2 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 3+4 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 3 name = firewire_pcm:00000ff200031248_LineIn 3+4 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 3
Jack: JackFFADODriver::Attach fCapturePortList[i] 3 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 3+4 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 4 name = firewire_pcm:00000ff200031248_LineIn 3+4 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 4
Jack: JackFFADODriver::Attach fCapturePortList[i] 4 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 5+6 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 5 name = firewire_pcm:00000ff200031248_LineIn 5+6 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 5
Jack: JackFFADODriver::Attach fCapturePortList[i] 5 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 5+6 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 6 name = firewire_pcm:00000ff200031248_LineIn 5+6 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 6
Jack: JackFFADODriver::Attach fCapturePortList[i] 6 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 7+8 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 7 name = firewire_pcm:00000ff200031248_LineIn 7+8 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 7
Jack: JackFFADODriver::Attach fCapturePortList[i] 7 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 7+8 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 8 name = firewire_pcm:00000ff200031248_LineIn 7+8 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 8
Jack: JackFFADODriver::Attach fCapturePortList[i] 8 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 9+10 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 9 name = firewire_pcm:00000ff200031248_LineIn 9+10 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 9
Jack: JackFFADODriver::Attach fCapturePortList[i] 9 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 9+10 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 10 name = firewire_pcm:00000ff200031248_LineIn 9+10 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 10
Jack: JackFFADODriver::Attach fCapturePortList[i] 10 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 11+12 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 11 name = firewire_pcm:00000ff200031248_LineIn 11+12 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 11
Jack: JackFFADODriver::Attach fCapturePortList[i] 11 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 11+12 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 12 name = firewire_pcm:00000ff200031248_LineIn 11+12 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 12
Jack: JackFFADODriver::Attach fCapturePortList[i] 12 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 13+14 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 13 name = firewire_pcm:00000ff200031248_LineIn 13+14 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 13
Jack: JackFFADODriver::Attach fCapturePortList[i] 13 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 13+14 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 14 name = firewire_pcm:00000ff200031248_LineIn 13+14 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 14
Jack: JackFFADODriver::Attach fCapturePortList[i] 14 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 15+16 left_in
Jack: JackGraphManager::AllocatePortAux port_index = 15 name = firewire_pcm:00000ff200031248_LineIn 15+16 left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 15
Jack: JackFFADODriver::Attach fCapturePortList[i] 15 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_LineIn 15+16 right_in
Jack: JackGraphManager::AllocatePortAux port_index = 16 name = firewire_pcm:00000ff200031248_LineIn 15+16 right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 16
Jack: JackFFADODriver::Attach fCapturePortList[i] 16 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_Main in (ch 17+18) left_in
Jack: JackGraphManager::AllocatePortAux port_index = 17 name = firewire_pcm:00000ff200031248_Main in (ch 17+18) left_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 17
Jack: JackFFADODriver::Attach fCapturePortList[i] 17 
firewire MSG: Registering audio capture port firewire_pcm:00000ff200031248_Main in (ch 17+18) right_in
Jack: JackGraphManager::AllocatePortAux port_index = 18 name = firewire_pcm:00000ff200031248_Main in (ch 17+18) right_in type = 32 bit float mono audio
Jack: JackConnectionManager::AddOutputPort ref = 0 port = 18
Jack: JackFFADODriver::Attach fCapturePortList[i] 18 
firewire MSG: Registering audio playback port firewire_pcm:00000ff200031248_Main out (ch 1+2) left_out
Jack: JackGraphManager::AllocatePortAux port_index = 19 name = firewire_pcm:00000ff200031248_Main out (ch 1+2) left_out type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 19
Jack: JackFFADODriver::Attach fPlaybackPortList[i] 19 
firewire MSG: Registering audio playback port firewire_pcm:00000ff200031248_Main out (ch 1+2) right_out
Jack: JackGraphManager::AllocatePortAux port_index = 20 name = firewire_pcm:00000ff200031248_Main out (ch 1+2) right_out type = 32 bit float mono audio
Jack: JackConnectionManager::AddInputPort ref = 0 port = 20
Jack: JackFFADODriver::Attach fPlaybackPortList[i] 20 
Jack: Clock source : system clock via clock_gettime
Jack: JackServer::Start
Jack: JackThreadedDriver::Start
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackThreadedDriver::Init IsRealTime
Jack: Create non RT thread
Jack: ThreadHandler: start
Jack: JackSocketServerChannel::ClientCreate socket
Jack: JackSocketServerChannel::BuildPoolTable size = 2
Jack: fSocketTable i = 1 fd = 44
Jack: fPollTable i = 1 fd = 44
Jack: JackRequest::Notification
Jack: JackEngine::NotifyClient: no callback for event = 4
Jack: JackEngine::NotifyClient: no callback for event = 4
Jack: JackGraphManager::RecalculateLatency port_index = 19
Jack: JackGraphManager::RecalculateLatency port_index = 20
Jack: JackGraphManager::RecalculateLatency port_index = 19
Jack: JackGraphManager::RecalculateLatency port_index = 20
Jack: JackGraphManager::RecalculateLatency port_index = 1
Jack: JackGraphManager::RecalculateLatency port_index = 2
Jack: JackGraphManager::RecalculateLatency port_index = 3
Jack: JackGraphManager::RecalculateLatency port_index = 4
Jack: JackGraphManager::RecalculateLatency port_index = 5
Jack: JackGraphManager::RecalculateLatency port_index = 6
Jack: JackGraphManager::RecalculateLatency port_index = 7
Jack: JackGraphManager::RecalculateLatency port_index = 8
Jack: JackGraphManager::RecalculateLatency port_index = 9
Jack: JackGraphManager::RecalculateLatency port_index = 10
Jack: JackGraphManager::RecalculateLatency port_index = 11
Jack: JackGraphManager::RecalculateLatency port_index = 12
Jack: JackGraphManager::RecalculateLatency port_index = 13
Jack: JackGraphManager::RecalculateLatency port_index = 14
Jack: JackGraphManager::RecalculateLatency port_index = 15
Jack: JackGraphManager::RecalculateLatency port_index = 16
Jack: JackGraphManager::RecalculateLatency port_index = 17
Jack: JackGraphManager::RecalculateLatency port_index = 18
Jack: JackGraphManager::RecalculateLatency port_index = 1
Jack: JackGraphManager::RecalculateLatency port_index = 2
Jack: JackGraphManager::RecalculateLatency port_index = 3
Jack: JackGraphManager::RecalculateLatency port_index = 4
Jack: JackGraphManager::RecalculateLatency port_index = 5
Jack: JackGraphManager::RecalculateLatency port_index = 6
Jack: JackGraphManager::RecalculateLatency port_index = 7
Jack: JackGraphManager::RecalculateLatency port_index = 8
Jack: JackGraphManager::RecalculateLatency port_index = 9
Jack: JackGraphManager::RecalculateLatency port_index = 10
Jack: JackGraphManager::RecalculateLatency port_index = 11
Jack: JackGraphManager::RecalculateLatency port_index = 12
Jack: JackGraphManager::RecalculateLatency port_index = 13
Jack: JackGraphManager::RecalculateLatency port_index = 14
Jack: JackGraphManager::RecalculateLatency port_index = 15
Jack: JackGraphManager::RecalculateLatency port_index = 16
Jack: JackGraphManager::RecalculateLatency port_index = 17
Jack: JackGraphManager::RecalculateLatency port_index = 18
10:27:20.864 Herunterfahr-Skript...
10:27:20.865 killall jackd
jack main caught signal 15
Jack: JackServer::Stop
Jack: JackThreadedDriver::Stop
Jack: JackPosixThread::Stop
Jack: ThreadHandler: exit
10:27:21.270 Herunterfahr-Skript beendet erfolgreich.
10:27:21.270 JACK fährt herunter...
Jack: JackServer::Close
Jack: JackPosixThread::Stop
Jack: fPollTable i = 1 fd = 44
Jack: JackRequest::Notification
Jack: JackRequest::Notification kQUIT
Jack: JackMachServerChannel::Execute JackQuitException
Jack: ThreadHandler: exit
Jack: JackServerSocket::Close /dev/shm/jack_(voreinst.)_1000_0
Jack: JackClientSocket::Close
Jack: JackFFADODriver::Detach
Jack: JackAudioDriver::Detach
Jack: JackGraphManager::DisconnectAllOutput port_index = 1 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 1 
Jack: JackGraphManager::DisconnectAllOutput port_index = 2 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 2 
Jack: JackGraphManager::DisconnectAllOutput port_index = 3 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 3 
Jack: JackGraphManager::DisconnectAllOutput port_index = 4 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 4 
Jack: JackGraphManager::DisconnectAllOutput port_index = 5 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 5 
Jack: JackGraphManager::DisconnectAllOutput port_index = 6 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 6 
Jack: JackGraphManager::DisconnectAllOutput port_index = 7 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 7 
Jack: JackGraphManager::DisconnectAllOutput port_index = 8 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 8 
Jack: JackGraphManager::DisconnectAllOutput port_index = 9 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 9 
Jack: JackGraphManager::DisconnectAllOutput port_index = 10 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 10 
Jack: JackGraphManager::DisconnectAllOutput port_index = 11 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 11 
Jack: JackGraphManager::DisconnectAllOutput port_index = 12 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 12 
Jack: JackGraphManager::DisconnectAllOutput port_index = 13 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 13 
Jack: JackGraphManager::DisconnectAllOutput port_index = 14 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 14 
Jack: JackGraphManager::DisconnectAllOutput port_index = 15 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 15 
Jack: JackGraphManager::DisconnectAllOutput port_index = 16 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 16 
Jack: JackGraphManager::DisconnectAllOutput port_index = 17 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 17 
Jack: JackGraphManager::DisconnectAllOutput port_index = 18 
Jack: JackConnectionManager::RemoveOutputPort ref = 0 port_index = 18 
Jack: JackGraphManager::DisconnectAllInput port_index = 19
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 19 
Jack: JackGraphManager::DisconnectAllInput port_index = 20
Jack: JackConnectionManager::RemoveInputPort ref = 0 port_index = 20 
Jack: JackDriver::Close
Jack: JackConnectionManager::DirectDisconnect last: ref1 = 0 ref2 = 0
Jack: JackGraphManager::DisconnectRefNum cur_index = 1 ref1 = 0 ref2 = 0
Jack: JackEngine::ClientCloseAux ref = 0
Jack: JackGraphManager::RemoveAllPorts ref = 0
Jack: JackPosixSemaphore::Destroy
Jack: JackDriver::Close
Jack: JackConnectionManager::DirectDisconnect last: ref1 = 1 ref2 = 1
Jack: JackGraphManager::DisconnectRefNum cur_index = 1 ref1 = 1 ref2 = 1
Jack: JackEngine::ClientCloseAux ref = 1
Jack: JackGraphManager::RemoveAllPorts ref = 1
Jack: JackPosixSemaphore::Destroy
Jack: JackEngine::Close
Jack: JackClientSocket::Close
Jack: no message buffer overruns
Jack: JackPosixThread::Stop
Jack: ThreadHandler: exit
Jack: Succeeded in unlocking 107302426 byte memory area
Jack: JackShmMem::delete size = 0 index = 4
Jack: ~JackDriver
no message buffer overruns
Jack: ~JackDriver
Jack: Succeeded in unlocking 994 byte memory area
Jack: JackShmMem::delete size = 0 index = 5
Jack: cleaning up shared memory
Jack: cleaning up files
Jack: unregistering server `(voreinst.)'
10:27:21.750 JACK wurde angehalten erfolgreich.
10:27:21.751 Nach-Herunterfahr-Skript...
10:27:21.751 pulsejackdisconnect
10:27:25.477 Nach-Herunterfahr-Skript beendet erfolgreich.
```

---

### Post by howefield on 2012-03-22
Thread moved to "*Other OS/Distro Talk*" forum.

---

