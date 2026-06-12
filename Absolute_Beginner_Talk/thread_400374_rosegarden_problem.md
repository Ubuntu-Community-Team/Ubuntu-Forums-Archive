---
title: "rosegarden problem"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by kaboom on 2007-04-03
Hey all, I've just installed rosegarden and when I open it using the terminal this is my output:

```
kaboom@kaboom:~$ rosegarden
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
rosegarden: main: Showing startup logo
kaboom@kaboom:~$ rosegarden (sequence manager): getSequencerPlugins - getting pl ugin information
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
[/home/kaboom/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa]
rosegarden (sequence manager): got 50000 pieces of plugin data at GUI side
Profiler : id = querying plugins - elapsed = 20ms CPU,  0.023993000R real
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
rosegarden (sequencer): SequencerMmapper : setting size of /tmp/kde-kaboom//rose garden_sequencer_timing_block to 91012
rosegarden (sequencer): SequencerMmapper : mmap size : 91012 at 0xb5fdc000
rosegarden (sequencer): SequencerMmapper::init()
rosegarden (sequencer): Registering with DCOP server
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.10

JackDriver::initialiseAudio - JACK server not running
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file o r directory
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: RosegardenGUIDoc::syncDevices - waiting for Sequencer to come up
rosegarden: couldn't kill any sequencer processes
rosegarden: RosegardenGUIApp::slotSequencerExited Sequencer exited
rosegarden: RosegardenGUIApp::queryExit
Profiler : id = RosegardenGUIDoc::syncDevices - elapsed = 90ms CPU,  61.23698400 0R real
rosegarden: RosegardenGUIDoc::openDocument(/usr/share/apps/rosegarden4/autoload. rg)
rosegarden: RosegardenGUIDoc[0x88b6748]::setModified(false)
rosegarden: RosegardenProgressDialog::RosegardenProgressDialog type 2 - Reading file... - modal : true
rosegarden: "zoomlevel" value = 38399
rosegarden (sequence manager): RoseXmlHandler::skipToNextPlayDevice; m_deviceRun ningId is 10000
rosegarden (sequence manager): RoseXmlHandler::skipToNextPlayDevice: fresh out o f devices
rosegarden (sequence manager): RoseXmlHandler::addMIDIDevice - can't call sequen cer addDevice
RosegardenGUIDoc::xmlParse (reader.parse()): 40ms elapsed
rosegarden: RosegardenGUIDoc::openDocument() end - m_composition : 0x88b67bc - m _composition->getNbSegments() : 0 - m_composition->getDuration() : 0
rosegarden: RosegardenGUIDoc[0x88b6748]::setModified(false)
rosegarden: RosegardenGUIApp::slotSequencerExited Sequencer exited
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3400232
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3400232
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x3400232

```


then an error message pops up saying the sequencer couldn't be started so sound recording will be unavailable this session.  After I hit ok rosegarden will open up but nothing i click responds.

i feel like i need a sequencer plugin but i dont have any idea where to get it.

any ideas on what I should do?

cheers 
chris

---

### Post by eric71 on 2007-04-04
You need to have the alsa sequencer module loaded, as well as the Jack sound server.  For jack, install Qjackctl with synaptic ans use this program to start jack.

For the alsa sequencer, see this:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

ALSA Sequencer

If you are planning on using MIDI at all, you will want to load the ALSA sequencer module. 
 sudo modprobe snd-seq

To have your system load it at bootup, you have to add it to the /etc/modules file. 
 sudo su -c 'echo snd-seq >> /etc/modules'

---

### Post by kaboom on 2007-04-04
that did it thanks for the help

---

