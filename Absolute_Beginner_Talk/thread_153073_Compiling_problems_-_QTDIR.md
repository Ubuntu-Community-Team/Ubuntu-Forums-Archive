---
title: "Compiling problems - QTDIR"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by stuoolong on 2006-03-31
Hello, I originally posted this in the compiling software section but there's been no replies after 3 days - I guessed it was maybe in the wrong place so I've moved it here. Mods, I hope that's ok.

I am trying to install a program from source, LMMS_0.1.4.

After ```
./configure
``` command, a short way in I get the following message:

```
checking QTDIR... configure: error: *** QTDIR must be defined, or --with-qtdir option given
```

As a newb, I have absolutely no idea what this means and searching the forums under QTDIR didn't give me much insight. I tried:

using the command ./configure --with-qtdir
Downloading the packages qt3-dev-tools, libqt3-mt, libqt3-mt-dpg and libqt3-mt-headers

None of this has helped. Can anyone offer any insight? Thanks in advance.

PS I have never successfully installed a program from source...

---

### Post by Sef on 2006-03-31
Did you download build-essential?  If not, you can't configure.

sudo apt-get updae

sudo apt-get install build-essential

---

### Post by stuoolong on 2006-03-31
Yes, I got build-essential.

---

### Post by stuoolong on 2006-03-31
Righty, I tried it again today, just out of curiosity thinking that a different day might bring a different solution...well it brought a different problem.

With no apparent difference, the ./configure worked this time :) BUT, when I got to the make command, there wre even more horible looking errors. Full output of make command is here:

```
/usr/bin/moc -o about_dialog.moc include/about_dialog.h
/usr/bin/moc -o arp_and_chords_tab_widget.moc include/arp_and_chords_tab_widget.h
/usr/bin/moc -o bb_editor.moc include/bb_editor.h
/usr/bin/moc -o bb_track.moc include/bb_track.h
/usr/bin/moc -o channel_track.moc include/channel_track.h
/usr/bin/moc -o combobox.moc include/combobox.h
/usr/bin/moc -o config_mgr.moc include/config_mgr.h
/usr/bin/moc -o cpuload_widget.moc include/cpuload_widget.h
/usr/bin/moc -o envelope_and_lfo_widget.moc include/envelope_and_lfo_widget.h
/usr/bin/moc -o envelope_tab_widget.moc include/envelope_tab_widget.h
/usr/bin/moc -o export_project_dialog.moc include/export_project_dialog.h
/usr/bin/moc -o fade_button.moc include/fade_button.h
/usr/bin/moc -o file_browser.moc include/file_browser.h
/usr/bin/moc -o group_box.moc include/group_box.h
/usr/bin/moc -o kmultitabbar.moc include/kmultitabbar.h
/usr/bin/moc -o kmultitabbar-qt3.moc include/kmultitabbar-qt3.h
/usr/bin/moc -o knob.moc include/knob.h
/usr/bin/moc -o lcd_spinbox.moc include/lcd_spinbox.h
/usr/bin/moc -o led_checkbox.moc include/led_checkbox.h
/usr/bin/moc -o lmms_main_win.moc include/lmms_main_win.h
/usr/bin/moc -o mixer.moc include/mixer.h
/usr/bin/moc -o name_label.moc include/name_label.h
/usr/bin/moc -o nstate_button.moc include/nstate_button.h
/usr/bin/moc -o midi_alsa_seq.moc include/midi_alsa_seq.h
/usr/bin/moc -o midi_tab_widget.moc include/midi_tab_widget.h
/usr/bin/moc -o pattern.moc include/pattern.h
/usr/bin/moc -o piano_roll.moc include/piano_roll.h
/usr/bin/moc -o piano_widget.moc include/piano_widget.h
/usr/bin/moc -o pixmap_button.moc include/pixmap_button.h
/usr/bin/moc -o plugin_browser.moc include/plugin_browser.h
/usr/bin/moc -o project_notes.moc include/project_notes.h
/usr/bin/moc -o rubberband.moc include/rubberband.h
/usr/bin/moc -o qxembed.moc include/qxembed.h
/usr/bin/moc -o rename_dialog.moc include/rename_dialog.h
/usr/bin/moc -o sample_buffer.moc include/sample_buffer.h
/usr/bin/moc -o sample_track.moc include/sample_track.h
/usr/bin/moc -o setup_dialog.moc include/setup_dialog.h
/usr/bin/moc -o side_bar.moc include/side_bar.h
/usr/bin/moc -o side_bar_widget.moc include/side_bar_widget.h
/usr/bin/moc -o song_editor.moc include/song_editor.h
/usr/bin/moc -o surround_area.moc include/surround_area.h
/usr/bin/moc -o tab_bar.moc include/tab_bar.h
/usr/bin/moc -o tab_button.moc include/tab_button.h
/usr/bin/moc -o tab_widget.moc include/tab_widget.h
/usr/bin/moc -o tempo_sync_knob.moc include/tempo_sync_knob.h
/usr/bin/moc -o timeline.moc include/timeline.h
/usr/bin/moc -o tool_button.moc include/tool_button.h
/usr/bin/moc -o track_container.moc include/track_container.h
/usr/bin/moc -o track.moc include/track.h
/usr/bin/moc -o visualization_widget.moc include/visualization_widget.h
make  all-recursive
make[1]: Entering directory `/usr/src/lmms-0.1.4'
Making all in artwork
make[2]: Entering directory `/usr/src/lmms-0.1.4/artwork'
Making all in track_icons
make[3]: Entering directory `/usr/src/lmms-0.1.4/artwork/track_icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/lmms-0.1.4/artwork/track_icons'
make[3]: Entering directory `/usr/src/lmms-0.1.4/artwork'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/usr/src/lmms-0.1.4/artwork'
make[2]: Leaving directory `/usr/src/lmms-0.1.4/artwork'
Making all in buildtools
make[2]: Entering directory `/usr/src/lmms-0.1.4/buildtools'
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -ansi -Wall -fno-exceptions -MT bin2res.o -MD -MP -MF ".deps/bin2res.Tpo" -c -o bin2res.o bin2res.cpp; \
then mv -f ".deps/bin2res.Tpo" ".deps/bin2res.Po"; else rm -f ".deps/bin2res.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CXX --mode=link g++  -g -O2 -ansi -Wall -fno-exceptions   -o bin2res  bin2res.o
mkdir .libs
g++ -g -O2 -ansi -Wall -fno-exceptions -o bin2res bin2res.o
make[2]: Leaving directory `/usr/src/lmms-0.1.4/buildtools'
Making all in locale
make[2]: Entering directory `/usr/src/lmms-0.1.4/locale'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/lmms-0.1.4/locale'
Making all in midi-maps
make[2]: Entering directory `/usr/src/lmms-0.1.4/midi-maps'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/lmms-0.1.4/midi-maps'
Making all in plugins
make[2]: Entering directory `/usr/src/lmms-0.1.4/plugins'
Making all in audio_file_processor
make[3]: Entering directory `/usr/src/lmms-0.1.4/plugins/audio_file_processor'
../../buildtools/bin2res artwork.png logo.png loop_off.png loop_on.png reverse_off.png reverse_on.png > embedded_resources.h
/usr/bin/moc -o audio_file_processor.moc audio_file_processor.h
make  all-am
make[4]: Entering directory `/usr/src/lmms-0.1.4/plugins/audio_file_processor'
if /bin/sh ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -I../../src/lib -I.    -DQT3 -I/usr/include/qt3 -D_REENTRANT -DQT_THREAD_SUPPORT -DPLUGIN_NAME="audiofileprocessor" -g -O2 -ansi -Wall -fno-exceptions -MT audio_file_processor.lo -MD -MP -MF ".deps/audio_file_processor.Tpo" -c -o audio_file_processor.lo audio_file_processor.cpp; \
then mv -f ".deps/audio_file_processor.Tpo" ".deps/audio_file_processor.Plo"; else rm -f ".deps/audio_file_processor.Tpo"; exit 1; fi
mkdir .libs
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -I../../src/lib -I. -DQT3 -I/usr/include/qt3 -D_REENTRANT -DQT_THREAD_SUPPORT -DPLUGIN_NAME=audiofileprocessor -g -O2 -ansi -Wall -fno-exceptions -MT audio_file_processor.lo -MD -MP -MF .deps/audio_file_processor.Tpo -c audio_file_processor.cpp  -fPIC -DPIC -o .libs/audio_file_processor.o
In file included from ../../include/qt3support.h:33,
                 from audio_file_processor.cpp:26:
/usr/include/qt3/qglobal.h:756:21: error: qconfig.h: No such file or directory
/usr/include/qt3/qglobal.h:766:22: error: qmodules.h: No such file or directory
../../include/mmp.h:45: error: invalid use of undefined type 'struct QDomDocument'
../../include/settings.h:36: error: forward declaration of 'struct QDomDocument'
../../include/mmp.h:99: error: field 'm_content' has incomplete type
../../include/mmp.h:100: error: field 'm_head' has incomplete type
../../include/mmp.h: In member function 'QDomElement& multimediaProject::content()':
../../include/mmp.h:73: error: 'm_content' was not declared in this scope
../../include/mmp.h: In member function 'QDomElement& multimediaProject::head()':
../../include/mmp.h:77: error: 'm_head' was not declared in this scope
../../include/lmms_main_win.h: At global scope:
../../include/lmms_main_win.h:76: error: ISO C++ forbids declaration of 'QWorkspace' with no type
../../include/lmms_main_win.h:76: error: 'QWorkspace' declared as an 'inline' field
../../include/lmms_main_win.h:76: error: expected ';' before '*' token
../../include/lmms_main_win.h:81: error: expected `;' before 'inline'
../../include/lmms_main_win.h:143: error: ISO C++ forbids declaration of 'QWorkspace' with no type
../../include/lmms_main_win.h:143: error: expected ';' before '*' token
../../include/config_mgr.h:73: error: invalid use of undefined type 'struct QDialog'
/usr/include/qt3/qwindowdefs.h:54: error: forward declaration of 'struct QDialog'
../../include/config_mgr.h:74: warning: 'class configManager' has virtual functions but non-virtual destructor
audio_file_processor.cpp: In member function 'virtual void audioFileProcessor::saveSettings(QDomDocument&, QDomElement&)':
audio_file_processor.cpp:295: error: variable 'QDomElement afp_de' has initializer but incomplete type
audio_file_processor.cpp:295: error: invalid use of undefined type 'struct QDomDocument'
../../include/settings.h:36: error: forward declaration of 'struct QDomDocument'
audio_file_processor.cpp:313: error: invalid use of undefined type 'struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'struct QDomElement'
audio_file_processor.cpp: In member function 'virtual void audioFileProcessor::loadSettings(const QDomElement&)':
audio_file_processor.cpp:321: error: invalid use of undefined type 'const struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:323: error: invalid use of undefined type 'const struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:325: error: invalid use of undefined type 'const struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:327: error: invalid use of undefined type 'const struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:329: error: invalid use of undefined type 'const struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:330: error: invalid use of undefined type 'const struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:331: error: invalid use of undefined type 'const struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:332: error: invalid use of undefined type 'const struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp:333: error: invalid use of undefined type 'const struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'const struct QDomElement'
audio_file_processor.cpp: In member function 'virtual void audioFileProcessor::dropEvent(QDropEvent*)':
audio_file_processor.cpp:453: error: invalid use of undefined type 'struct QDomElement'
../../include/settings.h:37: error: forward declaration of 'struct QDomElement'
/usr/include/qt3/private/qucom_p.h: At global scope:
/usr/include/qt3/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
make[4]: *** [audio_file_processor.lo] Error 1
make[4]: Leaving directory `/usr/src/lmms-0.1.4/plugins/audio_file_processor'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/usr/src/lmms-0.1.4/plugins/audio_file_processor'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/lmms-0.1.4/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lmms-0.1.4'
make: *** [all] Error 2 
```

The errors all seem to be related to things beginning with Q...qconfig.h, QDomelement, qt3 directory, structured QUtype...are all these things related?

---

### Post by stuoolong on 2006-04-02
*bump*

---

