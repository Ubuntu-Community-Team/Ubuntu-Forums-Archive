---
title: "RoseGarden no sona"
date: 2009-03-08
forum: Catalan Team
---

### Post by LitusMayol on 2009-03-08
Bones familia!

L'altre dia vaig instal·lar el **Rosegarden** i em vaig trobar amb aquest problema: no sona. Volia fer uns *MIDIs* per la universitat... i PAM! Em vaig trobar en que el programa funciona perfectament però no sona. Si exporto els fitxers a .*mid* els puc reproduir perfectament, però a l'hora d'editar i composar és molt i molt incòmode. 

Algú sap a què pot ser degut?


Us deixo traces de la consola que fa si només l'obro (sense el *jack*) i el tanco. Per si són útils
```
litus@mayolets-desktop:~$ rosegarden
litus@mayolets-desktop:~$ PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/litus/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 
LADSPAPluginFactory::discoverPlugins - done
PluginFactory::instance(ladspa): creating new LADSPAPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/litus/.ladspa] [/usr/local/lib/ladspa] [/usr/lib/ladspa] 
Rosegarden 1.7.0 - AlsaDriver [ALSA library version 1.0.17a, module version 1.0.17, kernel version 2.6.27-7-generic]

JackDriver::initialiseAudio - JACK server not running
LADSPAPluginFactory::discoverPlugins - done

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    128,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]

CREATED OUTPUT PORT 3:out 1 - MIDI software device for device 0
Connecting my port 3 to 128:0 on initialisation
done
Creating device 0 in Play mode for connection 128:0 TiMidity port 0 (write)
Default device name for this device is MIDI software device
CREATED OUTPUT PORT 4:out 2 - MIDI software device 2 for device 1
Connecting my port 4 to 128:1 on initialisation
done
Creating device 1 in Play mode for connection 128:1 TiMidity port 1 (write)
Default device name for this device is MIDI software device 2
CREATED OUTPUT PORT 5:out 3 - MIDI software device 3 for device 2
Connecting my port 5 to 128:2 on initialisation
done
Creating device 2 in Play mode for connection 128:2 TiMidity port 2 (write)
Default device name for this device is MIDI software device 3
CREATED OUTPUT PORT 6:out 4 - MIDI software device 4 for device 3
Connecting my port 6 to 128:3 on initialisation
done
Creating device 3 in Play mode for connection 128:3 TiMidity port 3 (write)
Default device name for this device is MIDI software device 4
CREATED OUTPUT PORT 7:out 5 - MIDI output system device for device 4
done
Creating device 4 in Play mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI output system device
Creating device 5 in Record mode for connection 14:0 Midi Through Port-0 (duplex) (not connecting)
Default device name for this device is MIDI input system device
AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 17, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.17 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 27, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.27-7-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

Composition::getTrackById(0) - WARNING - track id not found, this is probably a BUG /build/buildd/rosegarden-1.7.0/src/base/Composition.cpp:1539
Available track ids are: 
Renaming device 0 to General MIDI Device
Renamed 129:3 to General MIDI Device
CompositionModelImpl::slotInstrumentParametersChanged()
RosegardenGUIApp::awaitDialogClearance: entering
RosegardenGUIApp::awaitDialogClearance: exiting
Rosegarden: WARNING: No accurate sequencer timer available
RosegardenGUIApp::awaitDialogClearance: entering

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    128,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]

RosegardenGUIApp::awaitDialogClearance: exiting
TrackButtons::slotUpdateTracks
Comparing current version "1.7.0" with latest version "1.7.3"
RosegardenGUIApp::awaitDialogClearance: entering
RosegardenGUIApp::awaitDialogClearance: exiting
RosegardenSequencerApp::quit()
DataBlockRepository::clear()
SoundDriver::~SoundDriver (exiting)
AudioPlayQueue::~AudioPlayQueue()
Toodle-pip.
Warning: Composition::~Composition() with 2 observers still extant
Observers are: 0xb526bd0c [N10Rosegarden19SegmentParameterBoxE] 0xb4f08670 [N10Rosegarden20CompositionModelImplE]

litus@mayolets-desktop:~$ 

```

---

### Post by RainCT on 2009-03-08
Crec que el Rosegarden només funciona amb Jack (que no és gaire divertit de fer anar :P). He trobat aquestes instruccions, prova a veure si et funcionen: [http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

---

### Post by CarlesOriol on 2009-03-09
Recorda que el timidity és un sintetitzador per programari i per reproduir en temps real, tal i com et cal per composar i fer arranjaments, té una carencia brutal.

A més amb les proves que jo he fet produeix canvis en el temps (s'allarga i es retrassa).

No et puc ajudar amb el problema, però crec que et cal una targeta amb sintetitzador per maquinari o bé un controlador midi amb un dispositiu extern.

---

### Post by LitusMayol on 2009-03-17
Bones!

Doncs a veure, **Sigrfrid** el *Jack* ja el sabia fer anar, però amb aquest manual he acabat d'ajustar-lo a les meves necessitats. El que em comentes del amic *Timidity*, **CarlesOriol**, a mi també em passa: se'm retassa molt de vegades (*Tuxguitar*) o simplement no funciona (*Rosegarden*). 

Seguiré buscant (miraré més pel camí de les targetes i dels controladors MIDI). 

Si ho resolc o esbrino res de nou: ho penjaré! ,9

Merci de totes maneres!

---

