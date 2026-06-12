---
title: "X server trouble"
date: 2008-03-02
forum: Arch and derivatives
---

### Post by jargs on 2008-03-02
I am using the catalyst driver and a couple of days ago i used the exact same method but it worked fine. I did an "Xorg -configure", then copied the file over to "/etc/X11/xorg.conf", then i ran aticonfig with this command "aticonfig --initial=dual-head --input=/etc/X11/xorg.conf" and "aticonfig --dtop=horizontal --overlay-on=1". I also have a ~/.xinitrc file which reads "exec xterm". Now when i try and start X my right monitor looses connection and my left monitor remains blank, I cannot exit out of this unless I reboot the machine. This is really confusing me, anyone know what could be causing it or anything i might have forgotten to do? Thanks.

---

### Post by jargs on 2008-03-02
Here is my xorg:
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/usr/share/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/misc"
	FontPath     "/usr/share/fonts/100dpi:unscaled"
	FontPath     "/usr/share/fonts/75dpi:unscaled"
	FontPath     "/usr/share/fonts/TTF"
	FontPath     "/usr/share/fonts/Type1"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "dbe"
	Load  "extmod"
	Load  "record"
	Load  "dri"
	Load  "xtrap"
	Load  "freetype"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "NoDRI"              	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "DRM_nbufs"          	# <i>
        #Option     "DRM_bufsize"        	# <i>
        #Option     "Capabilities"       	# <i>
        #Option     "CapabilitiesEx"     	# <i>
        #Option     "ClientDriverName"   	# [<str>]
        #Option     "KernelModuleParm"   	# [<str>]
        #Option     "AGPMask"            	# <i>
        #Option     "AGPv3Mask"          	# <i>
        #Option     "BufferTiling"       	# [<bool>]
        #Option     "Profile"            	# <str>
        #Option     "RingSize"           	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "GammaCorrectionI"   	# <i>
        #Option     "GammaCorrectionII"  	# <i>
        #Option     "OpenGLOverlay"      	# [<bool>]
        #Option     "DefaultVisualTrueColor" 	# [<bool>]
        #Option     "VideoOverlay"       	# [<bool>]
        #Option     "DesktopSetup"       	# [<str>]
        #Option     "MonitorLayout"      	# [<str>]
        #Option     "ForceMonitors"      	# [<str>]
        #Option     "EnableMonitor"      	# <str>
        #Option     "OverlayOnCRTC2"     	# [<bool>]
        #Option     "Mode2"              	# [<str>]
        #Option     "PairModes"          	# [<str>]
        #Option     "HSync2"             	# [<str>]
        #Option     "VRefresh2"          	# [<str>]
        #Option     "ScreenOverlap"      	# <i>
        #Option     "MemClock"           	# <i>
        #Option     "ASICClock"          	# <i>
        #Option     "UseInternalAGPGART" 	# [<bool>]
        #Option     "FastSwap"           	# [<bool>]
        #Option     "Stereo"             	# [<bool>]
        #Option     "StereoSyncEnable"   	# <i>
        #Option     "DisableOvScaler"    	# [<bool>]
        #Option     "UseFastTLS"         	# <i>
        #Option     "BlockSignalsOnLock" 	# [<bool>]
        #Option     "ForceGenericCPU"    	# [<bool>]
        #Option     "CenterMode"         	# [<bool>]
        #Option     "OffScreenPixmaps"   	# [<bool>]
        #Option     "EnableOpaqueOverlayVisual" 	# [<bool>]
        #Option     "TMDSCoherentMode"   	# [<bool>]
        #Option     "EnablePrivateBackZ" 	# [<bool>]
        #Option     "TVFormat"           	# [<str>]
        #Option     "TVStandard"         	# [<str>]
        #Option     "TVOverscan"         	# [<bool>]
        #Option     "TVHSizeAdj"         	# <i>
        #Option     "TVVSizeAdj"         	# <i>
        #Option     "TVHPosAdj"          	# <i>
        #Option     "TVVPosAdj"          	# <i>
        #Option     "TVHStartAdj"        	# <i>
        #Option     "TVColorAdj"         	# <i>
        #Option     "PseudoColorVisuals" 	# [<bool>]
        #Option     "PreferredVRefresh"  	# <i>
        #Option     "FastStart"          	# [<bool>]
        #Option     "ProfileDriver"      	# [<bool>]
        #Option     "PPPTforGART"        	# [<bool>]
        #Option     "TexturedVideo"      	# [<bool>]
        #Option     "TexturedVideoSync"  	# [<bool>]
        #Option     "Textured2D"         	# [<bool>]
        #Option     "TexturedXrender"    	# [<bool>]
        #Option     "DPMS"               	# [<bool>]
        #Option     "MaxGARTSize"        	# <i>
        #Option     "LogoPosX"           	# <i>
        #Option     "LogoPosY"           	# <i>
        #Option     "LogoColFG"          	# <i>
        #Option     "LogoColBG"          	# <i>
        #Option     "SwapScreens"        	# [<bool>]
        #Option     "FBC"                	# [<bool>]
        #Option     "FrontBufferMode"    	# <i>
        #Option     "BackBufferMode"     	# <i>
        #Option     "DepthBufferMode"    	# <i>
        #Option     "OverlayBufferMode"  	# <i>
        #Option     "VideoOverlayBufferMode" 	# <i>
        #Option     "EnableIrqMgr"       	# [<bool>]
        #Option     "EnableMulticard"    	# [<bool>]
        #Option     "EnablePPLIB"        	# [<bool>]
        #Option     "DefaultOnDC"        	# [<bool>]
	Identifier  "Card0"
	Driver      "fglrx"
	VendorName  "ATI Technologies Inc"
	BoardName   "RV570 [Radeon X1950 Pro]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

