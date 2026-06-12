---
title: "secondlife"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by serene on 2007-08-31
I am new to ubuntu and tried to install the linux version of secondlife from secondlife.com. This is the error msg I got.

2007-08-31T10:59:35Z INFO: another_instance_running: Checking marker file for lo ck...
2007-08-31T10:59:35Z INFO: another_instance_running: Marker file isn't locked.
2007-08-31T10:59:35Z INFO: init_marker_file: Checking marker file for lock...
2007-08-31T10:59:35Z INFO: init_marker_file: Marker file created.
2007-08-31T10:59:35Z INFO: init_marker_file: Removing message.log
2007-08-31T10:59:35Z INFO: Exiting init_marker_file().
2007-08-31T10:59:35Z INFO: write_debug: Opening debug file /home/julie/.secondli fe/logs/debug_info.log
2007-08-31T10:59:35Z INFO: write_system_info: Second Life version 1.18.1
2007-08-31T10:59:35Z INFO: write_system_info: Local time: 2007-08-31T06:59:35 ED T
2007-08-31T10:59:35Z INFO: write_system_info: CPU info:
processor       : 0 vendor_id   : AuthenticAMD cpu family       : 15 model     :  95 model name  : AMD Athlon(tm) 64 Processor 3800+ stepping    : 2 cpu MHz    :  2405.183 cache size    : 512 KB fdiv_bug       : no hlt_bug            : no f00 f_bug   : no coma_bug   : no fpu                : yes fpu_exception     : yes cp uid level       : 1 wp          : yes flags             : fpu vme de pse tsc msr  pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 sysc all nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm bogomips      : 4814.2 8
->mHasSSE:     1
->mHasSSE2:    1
->mHasAltivec: 0
->mCPUMhz:     2405
->mCPUString:  AMD Athlon(tm) 64 Processor 3800+

2007-08-31T10:59:35Z INFO: write_system_info: Memory info:
MemTotal:       905032 kB MemFree:        256792 kB Buffers:         15596 kB Ca ched:         366320 kB SwapCached:      17884 kB Active:         396408 kB Inac tive:       196644 kB HighTotal:           0 kB HighFree:            0 kB LowTot al:       905032 kB LowFree:        256792 kB SwapTotal:     2650684 kB SwapFree :      2631776 kB Dirty:             108 kB Writeback:           0 kB Mapped:       260776 kB Slab:            35220 kB CommitLimit:   3103200 kB Committed_AS :   530708 kB PageTables:       2424 kB VmallocTotal:   114680 kB VmallocUsed:    15660 kB VmallocChunk:    98436 kB
2007-08-31T10:59:35Z INFO: write_system_info: OS info: Linux 2.6.15-28-386 #1 PR EEMPT Wed Jul 18 22:50:32 UTC 2007 i686
2007-08-31T10:59:35Z INFO: main: Loading feature tables.
2007-08-31T10:59:35Z INFO: main: Loading configuration file /home/julie/.secondl ife/user_settings/settings.xml
2007-08-31T10:59:35Z WARNING: parseFile: Couldn't open file /home/julie/.secondl ife/user_settings/settings.xml
2007-08-31T10:59:35Z WARNING: parseFile: LLXmlTree parse failed.  Line 1: Couldn 't open file /home/julie/.secondlife/user_settings/settings.xml
2007-08-31T10:59:35Z WARNING: loadFromFile: Unable to open control file /home/ju lie/.secondlife/user_settings/settings.xml
2007-08-31T10:59:35Z INFO: main: Failed to load settings from /home/julie/.secon dlife/user_settings/settings.xml
2007-08-31T10:59:35Z INFO: main: Loading legacy settings from /home/julie/.secon dlife/user_settings/settings.ini
2007-08-31T10:59:35Z INFO: loadFromFileLegacy: LLControlGroup::loadFromFile unab le to open.
2007-08-31T10:59:35Z WARNING: parseFile: Couldn't open file /home/julie/.secondl ife/user_settings/crash_settings.xml
2007-08-31T10:59:35Z WARNING: parseFile: LLXmlTree parse failed.  Line 1: Couldn 't open file /home/julie/.secondlife/user_settings/crash_settings.xml
2007-08-31T10:59:35Z WARNING: loadFromFile: Unable to open control file /home/ju lie/.secondlife/user_settings/crash_settings.xml
2007-08-31T10:59:35Z INFO: main: Loading art table from /home/julie/Desktop/Seco ndLife_i686_1_18_1_2/app_settings/viewerart.xml
2007-08-31T10:59:35Z INFO: main: Loading art table from /home/julie/Desktop/Seco ndLife_i686_1_18_1_2/skins/textures/textures.xml
2007-08-31T10:59:35Z INFO: main: Loading base colors from /home/julie/Desktop/Se condLife_i686_1_18_1_2/app_settings/colors_base.xml
2007-08-31T10:59:35Z INFO: main: Loading user colors from /home/julie/Desktop/Se condLife_i686_1_18_1_2/app_settings/colors.xml
2007-08-31T10:59:35Z INFO: main: Failed to load user colors from /home/julie/Des ktop/SecondLife_i686_1_18_1_2/app_settings/colors.xml
2007-08-31T10:59:35Z INFO: main: Loading legacy colors from /home/julie/Desktop/ SecondLife_i686_1_18_1_2/app_settings/colors.ini
2007-08-31T10:59:35Z INFO: update_vector_performances: Vectorization         : D ISABLED
2007-08-31T10:59:35Z INFO: update_vector_performances: Vector Processor      : C OMPILER DEFAULT
2007-08-31T10:59:35Z INFO: update_vector_performances: Vectorized Skinning   : D ISABLED
2007-08-31T10:59:35Z INFO: purge_cache: Purging Texture Cache...
2007-08-31T10:59:35Z WARNING: ll_apr_file_remove failed on file: /home/julie/.se condlife/cache/texture.cache
2007-08-31T10:59:35Z WARNING: ll_apr_file_remove failed on file: /home/julie/.se condlife/cache/textures/texture.entries
2007-08-31T10:59:35Z INFO: purge_cache: Purging Cache...
2007-08-31T10:59:35Z INFO: initCache: TEXTURE CACHE: Headers: 139810 Textures si ze: 320 MB
2007-08-31T10:59:35Z INFO: init_cache: VFS CACHE SIZE: 100 MB
2007-08-31T10:59:35Z WARNING: init_cache: Bad or missing vfx index file /home/ju lie/.secondlife/cache/index.db2.x.1
2007-08-31T10:59:35Z WARNING: init_cache: Removing old vfs data file /home/julie /.secondlife/cache/data.db2.x.1
2007-08-31T10:59:35Z INFO: init_cache: Removing old vfs and re-sizing
2007-08-31T10:59:35Z INFO: presizeDataFile: Pre-sized VFS data file to 104857600  bytes
2007-08-31T10:59:35Z INFO: LLVFS: VFS: Using index file /home/julie/.secondlife/ cache/index.db2.x.511342647 and data file /home/julie/.secondlife/cache/data.db2 .x.511342647
2007-08-31T10:59:35Z INFO: LLVFS: VFS: Using index file /home/julie/Desktop/Seco ndLife_i686_1_18_1_2/app_settings/static_index.db2 and data file /home/julie/Des ktop/SecondLife_i686_1_18_1_2/app_settings/static_data.db2
2007-08-31T10:59:35Z INFO: main: Initializing window...
2007-08-31T10:59:35Z INFO: ll_try_gtk_init: Starting GTK Initialization.
2007-08-31T10:59:35Z INFO: ll_try_gtk_init: GTK Initialized.
2007-08-31T10:59:35Z INFO: ll_try_gtk_init: - Compiled against GTK version 2.4.1 4
2007-08-31T10:59:35Z INFO: ll_try_gtk_init: - Running against GTK version 2.8.20
2007-08-31T10:59:35Z INFO: createContext, fullscreen=0 size=800x600
2007-08-31T10:59:35Z INFO: createContext: Compiled against SDL 1.2.5
2007-08-31T10:59:35Z INFO: createContext:  Running against SDL 1.2.12
2007-08-31T10:59:35Z INFO: createContext: creating window 800x600x32
2007-08-31T10:59:35Z WARNING: createContext: window creation failure. SDL: Could n't find matching GLX visual
2007-08-31T10:59:35Z INFO: destroyContext begins
2007-08-31T10:59:35Z INFO: destroyContext: shutdownGL begins
2007-08-31T10:59:35Z INFO: destroyContext: SDL_QuitSS/VID begins
2007-08-31T10:59:35Z INFO: OSMessageBoxSDL: Creating a dialog because we're in w indowed mode and GTK is happy.
2007-08-31T10:59:38Z INFO: Skipping quitCursors: mWindow already gone.
2007-08-31T10:59:38Z INFO: destroyContext begins
2007-08-31T10:59:38Z INFO: destroyContext: shutdownGL begins
2007-08-31T10:59:38Z INFO: destroyContext: SDL_QuitSS/VID begins
2007-08-31T10:59:38Z WARNING: createWindow: LLWindowManager::create() : Error cr eating window.
2007-08-31T10:59:38Z WARNING: LLViewerWindow: Unable to create window, be sure s creen is set at 32-bit color and your graphics driver is configured correctly. See README-linux.txt or README-solaris.txt for further information.
2007-08-31T10:59:38Z INFO: remove_marker_file()
*** glibc detected *** double free or corruption (!prev): 0x0b1ea0f0 ***

can someone help install it correctly please?

The help file from secondlife says

5. TROUBLESHOOTING
-=-=-=-=-=-=-=-=-=

The client prints a lot of diagnostic information to the console it was
run from.  Most of this is also replicated in ~/.secondlife/logs/SecondLife.log
- this is helpful to read when troubleshooting, especially 'WARNING' lines.

PROBLEM 1:- Second Life fails to start up, with a warning on the console like:
   'Error creating window.' or
   'Unable to create window, be sure screen is set at 32-bit color' or
   'SDL: Couldn't find matching GLX visual.'
SOLUTION:- Usually this indicates that your graphics card does not meet
   the minimum requirements, or that your system's OpenGL 3D graphics driver is
   not updated and configured correctly.  If you believe that your graphics
   card DOES meet the minimum requirements then you likely need to install the
   official so-called 'non-free' nVidia or ATI (fglrx) graphics drivers; we
   suggest one of the following options:
 * Consult your Linux distribution's documentation for installing these
   official drivers.  For example, Ubuntu provides documentation here:
   <https://help.ubuntu.com/community/BinaryDriverHowto>
 * If your distribution does not make it easy, then you can download the
   required Linux drivers straight from your graphics card manufacturer:
   - nVidia cards: <http://www.nvidia.com/object/unix.html>
   - ATI cards: <http://ati.amd.com/support/driver.html>

There are several drivers available at nvidia but I don't know how to figure out which one I need

---

### Post by jclmusic on 2007-08-31
looks like u might need the proprietary drivers to run it.

---

### Post by wenid on 2007-12-11
The original poster may well have solved this by now, but for anyone else with a similar issue, you need one of the "nvidia-glx" restricted packages. nvidia-glx-new works for my not-so-new GeForce 6150. Note that as of Gutsy, the nvidia-settings package "recommended" by nvidia-glx-new actually conflicts with nvidia-glx-new and prompts you to install nvidia-glx-legacy instead :confused:

---

