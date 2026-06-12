---
title: "Xsession errors with mbp5"
date: 2011-07-19
forum: Apple Hardware Users
---

### Post by silverhawk_184 on 2011-07-19
Hello

I have an install of LinuxMint 11 on my MBP5, and have all the mactel drivers loaded.

I am getting a hard time getting the compiz animations to work. Only wobbly windows and rotate cube work. I used the compiz-config wizard.

Also, I have a displayport to dvi cable, that is supposed to work with the mac, but has a hard time initializing the monitor. If I use a Apple dp>dvi adapter and initialize the monitor in nvidia-config and then swap the cable to my amazon one it works fine. Also, if I do a brand new oob install of Linux Mint it works just fine. EDIT: Upon gathering my xsession.errors log (startup>delete xsession.errors file>ctrl+alt+backspace) my monitor came up fine. odd!

Also, Evolution wants me to put my password in at every new window. It is connected to a LAN exchange server. I cannot get main-notifications to work either, the plugin "Jean-Yves Lefort's Mail Notification" checkbox cannot be enabled.

Thanks in advance.

xsession.errors
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
GNOME_KEYRING_CONTROL=/tmp/keyring-g8p5X6
GNOME_KEYRING_CONTROL=/tmp/keyring-g8p5X6
GNOME_KEYRING_CONTROL=/tmp/keyring-g8p5X6
SSH_AUTH_SOCK=/tmp/keyring-g8p5X6/ssh
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
** Message: adding killswitch idx 1 state KILLSWITCH_STATE_UNBLOCKED
** Message: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
Initializing opengl options...done
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
Initializing decor options...done
/usr/bin/compiz (core) - Error: Plugin 'text' not loaded.

/usr/bin/compiz (ring) - Warn: No compatible text plugin loaded
Initializing ring options...done
** (bluetooth-applet:15291): DEBUG: Unhandled UUID 453994d5-d58b-96f9-6616-b37f586ba2ec (0x453994d5)
** (bluetooth-applet:15291): DEBUG: Unhandled UUID 936da01f-9abd-4d9d-80c7-02af85c822a8 (0x936da01f)
** Message: killswitch 1 is KILLSWITCH_STATE_UNBLOCKED
** Message: killswitches state KILLSWITCH_STATE_UNBLOCKED
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
/home/silver/.gtkrc-2.0:5: /home/silver/.gtkrc-2.0:5: /home/silver/.gtkrc-2.0:5: error: error: invalid string constant "override-ctrl-f", expected valid string constant
invalid string constant "override-ctrl-f", expected valid string constant
error: invalid string constant "override-ctrl-f", expected valid string constant
Initializing animation options...done

ERROR: Cannot open display 'silver-linux:0.0'.


ERROR: Unable to assign attribute CursorShadow specified on line 22 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 23 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 24 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 25 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 26 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 27
       of configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 28
       of configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 29 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 30 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 31 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 32 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 33 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 34 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line
       35 of configuration file '/home/silver/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 36
       of configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 37 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 38 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 39 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 40 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 41 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 42 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 43 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 44 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 45 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 46 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute DigitalVibrance specified on line 47 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 48 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OverscanCompensation specified on line 49
       of configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ColorSpace specified on line 50 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ColorRange specified on line 51 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureBrightness specified on line
       52 of configuration file '/home/silver/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoTextureContrast specified on line
       53 of configuration file '/home/silver/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoTextureHue specified on line 54 of
       configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSaturation specified on line
       55 of configuration file '/home/silver/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on
       line 56 of configuration file '/home/silver/.nvidia-settings-rc' (no
       Display connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 57
       of configuration file '/home/silver/.nvidia-settings-rc' (no Display
       connection).

Initializing move options...done
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
Initializing imgjpeg options...done
Initializing gnomecompat options...done
gnome-session[15178]: WARNING: Could not launch application 'nm-applet.desktop': Unable to start application: Failed to execute child process "nm-applet" (No such file or directory)
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
Initializing grid options...done
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
/usr/share/blueproximity/proximity.py:186: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.wTree = gtk.glade.XML(self.gladefile)
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
Initializing vpswitch options...done
Initializing resize options...done
/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
Initializing place options...done
** (process:15287): DEBUG: zeitgeist-datahub.vala:174: Inserting 108 events
Initializing workarounds options...done
Initializing wobbly options...done
Initializing mousepoll options...done
Initializing animationaddon options...done
I/O warning : failed to load external entity "/home/silver/.compiz/session/106a4b3fd6e780a622131108452119824500000151780034"
Initializing session options...done
/usr/bin/compiz (core) - Error: Plugin 'text' not loaded.

/home/silver/.gtkrc-2.0:5: error: invalid string constant "override-ctrl-f", expected valid string constant
Initializing thumbnail options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing addhelper options...done
Initializing cube options...done
Initializing rotate options...done
/usr/lib/linuxmint/mintUpdate/mintUpdate.py:1721: GtkWarning: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
  gtk.main()

(bluetooth-applet:15291): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed

(gnome-power-manager:15312): Gdk-CRITICAL **: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
/usr/share/blueproximity/proximity.py:1299: GtkWarning: IA__gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freeze_count > 0' failed
  gtk.main()
Initializing nautilus-dropbox 0.6.8
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension
Initializing nautilus-ideviceinfo extension
Setting Update "command"
Setting Update "minimize_effects"
Setting Update "minimize_durations"
Setting Update "minimize_matches"
Setting Update "outline_color"
Setting Update "fill_color"
Setting Update "border_color"
Setting Update "fill_color"
Setting Update "multioutput_mode"
Setting Update "skydome_image"
Setting Update "raise_on_rotate"
Setting Update "snap_top"
Setting Update "zoom"
** (process:15287): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/silver/.xsession-errors
** (process:15287): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:15287): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>!' for action 'SetBookmark1'
  windowdata["action_group"].add_actions(actions, window)
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>@' for action 'SetBookmark2'
  windowdata["action_group"].add_actions(actions, window)
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>#' for action 'SetBookmark3'
  windowdata["action_group"].add_actions(actions, window)
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>$' for action 'SetBookmark4'
  windowdata["action_group"].add_actions(actions, window)
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>%' for action 'SetBookmark5'
  windowdata["action_group"].add_actions(actions, window)
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>^' for action 'SetBookmark6'
  windowdata["action_group"].add_actions(actions, window)
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>&' for action 'SetBookmark7'
  windowdata["action_group"].add_actions(actions, window)
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>*' for action 'SetBookmark8'
  windowdata["action_group"].add_actions(actions, window)
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>(' for action 'SetBookmark9'
  windowdata["action_group"].add_actions(actions, window)
/home/silver/.gnome2/gedit/plugins/line_tools.py:121: GtkWarning: Unable to parse accelerator '<Control>)' for action 'SetBookmark0'
  windowdata["action_group"].add_actions(actions, window)
** (process:15287): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:15287): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:15287): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (deja-dup-monitor:15304): DEBUG: monitor.vala:263: Invalid next run date.  Not scheduling a backup.

```

.nvidia-settings-rc
```

#
# /home/silver/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Tue Jul 12 09:02:12 2011
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = Yes
ShowQuitDialog = Yes
Timer = Graphics_Card_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

silver-linux:0.0/CursorShadow=0
silver-linux:0.0/CursorShadowAlpha=64
silver-linux:0.0/CursorShadowRed=0
silver-linux:0.0/CursorShadowGreen=0
silver-linux:0.0/CursorShadowBlue=0
silver-linux:0.0/CursorShadowXOffset=4
silver-linux:0.0/CursorShadowYOffset=2
silver-linux:0.0/SyncToVBlank=0
silver-linux:0.0/LogAniso=0
silver-linux:0.0/FSAA=0
silver-linux:0.0/TextureSharpen=0
silver-linux:0.0/AllowFlipping=1
silver-linux:0.0/FSAAAppControlled=1
silver-linux:0.0/LogAnisoAppControlled=1
silver-linux:0.0/OpenGLImageSettings=1
silver-linux:0.0/FSAAAppEnhanced=0
silver-linux:0.0/RedBrightness=0.000000
silver-linux:0.0/GreenBrightness=0.000000
silver-linux:0.0/BlueBrightness=0.000000
silver-linux:0.0/RedContrast=0.000000
silver-linux:0.0/GreenContrast=0.000000
silver-linux:0.0/BlueContrast=0.000000
silver-linux:0.0/RedGamma=1.000000
silver-linux:0.0/GreenGamma=1.000000
silver-linux:0.0/BlueGamma=1.000000
silver-linux:0.0/DigitalVibrance[DFP-0]=0
silver-linux:0.0/GPUScaling[DFP-0]=131073
silver-linux:0.0/OverscanCompensation[DFP-0]=0
silver-linux:0.0/ColorSpace[DFP-0]=0
silver-linux:0.0/ColorRange[DFP-0]=0
silver-linux:0.0/XVideoTextureBrightness=0
silver-linux:0.0/XVideoTextureContrast=0
silver-linux:0.0/XVideoTextureHue=0
silver-linux:0.0/XVideoTextureSaturation=0
silver-linux:0.0/XVideoTextureSyncToVBlank=1
silver-linux:0.0/XVideoSyncToDisplay=65536

```

xorg.conf
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Mon Apr 18 15:14:00 PDT 2011

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@allspice)  Fri Feb 25 14:42:07 UTC 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Apple"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1280+0"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

compiz.profile
```

[move]
s0_initiate_button = <Alt>Button1
s0_initiate_key = <Alt>F7
s0_opacity = 100
s0_constrain_y = true
s0_snapoff_maximized = true
s0_lazy_positioning = true

[expo]
s0_expo_key = <Super>s
s0_expo_button = Disabled
s0_expo_edge = 
s0_double_click_time = 500
s0_dnd_button = Button1
s0_exit_button = Button3
s0_next_vp_button = Button5
s0_prev_vp_button = Button4
s0_zoom_time = 0.300000
s0_expo_immediate_move = false
s0_expo_animation = 0
s0_deform = 0
s0_distance = 0.000000
s0_vp_distance = 0.800000
s0_aspect_ratio = 1.000000
s0_curve = 0.500000
s0_hide_docks = false
s0_mipmaps = false
s0_multioutput_mode = 0
s0_vp_brightness = 80.000000
s0_vp_saturation = 100.000000
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_scale_factor = 1.000000

[reflex]
s0_file = reflection.png
s0_match = any
s0_window = true
s0_decoration = true
s0_threshold = 1
s0_moving = true

[imgjpeg]
s0_quality = 80

[wallpaper]
s0_bg_image = /home/silver/Downloads/133200-1.jpg;/home/silver/Downloads/133507-1.jpg;/home/silver/Downloads/135419-1.jpg;/home/silver/Downloads/136190-1.jpg;/home/silver/Downloads/139978-1.jpg;/home/silver/Downloads/140126-1.png;
s0_bg_image_pos = 0;0;0;0;0;0;
s0_bg_fill_type = 0;0;0;0;0;0;
s0_bg_color1 = #000000ff;#000000ff;#000000ff;#000000ff;#000000ff;#000000ff;
s0_bg_color2 = #000000ff;#000000ff;#000000ff;#000000ff;#000000ff;#000000ff;
s0_cycle_wallpapers = true
s0_cycle_timeout = 10.000000
s0_fade_duration = 2.000000

[winrules]
s0_skiptaskbar_match = 
s0_skippager_match = 
s0_above_match = 
s0_below_match = 
s0_sticky_match = 
s0_fullscreen_match = 
s0_maximize_match = 
s0_no_argb_match = 
s0_no_move_match = 
s0_no_resize_match = 
s0_no_minimize_match = 
s0_no_maximize_match = 
s0_no_close_match = 
s0_no_focus_match = 
s0_size_matches = 
s0_size_width_values = 
s0_size_height_values = 

[gnomecompat]
s0_main_menu_key = <Alt>F1
s0_run_key = <Alt>F2
s0_command_screenshot = gnome-screenshot
s0_run_command_screenshot_key = Print
s0_command_window_screenshot = gnome-screenshot --window
s0_run_command_window_screenshot_key = <Alt>Print
s0_command_terminal = gnome-terminal
s0_run_command_terminal_key = Disabled

[detection]
s0_detect_bad_pci = true
s0_detect_bad_drivers = true

[grid]
s0_put_center_key = <Control><Alt>KP_5
s0_put_left_key = <Control><Alt>KP_4
s0_put_right_key = <Control><Alt>KP_6
s0_put_top_key = <Control><Alt>KP_8
s0_put_bottom_key = <Control><Alt>KP_2
s0_put_topleft_key = <Control><Alt>KP_7
s0_put_topright_key = <Control><Alt>KP_9
s0_put_bottomleft_key = <Control><Alt>KP_1
s0_put_bottomright_key = <Control><Alt>KP_3
s0_put_maximize_key = <Control><Alt>KP_0
s0_put_restore_key = <Control><Alt>r
s0_top_left_corner_action = 4
s0_top_edge_action = 10
s0_top_right_corner_action = 6
s0_left_edge_action = 4
s0_right_edge_action = 6
s0_bottom_left_corner_action = 4
s0_bottom_edge_action = 0
s0_bottom_right_corner_action = 6
s0_snapoff_maximized = false
s0_snapback_windows = true
s0_left_edge_threshold = 15
s0_right_edge_threshold = 15
s0_top_edge_threshold = 20
s0_bottom_edge_threshold = 5
s0_draw_indicator = true
s0_outline_color = #a9fb009f
s0_fill_color = #abfb004f
s0_indicator_direction = 0
s0_indicator_type = 0
s0_behind_window = true

[staticswitcher]
s0_next_button = Disabled
s0_next_key = <Alt>Tab
s0_prev_button = Disabled
s0_prev_key = <Shift><Alt>Tab
s0_next_all_button = Disabled
s0_next_all_key = <Control><Alt>Tab
s0_prev_all_button = Disabled
s0_prev_all_key = <Shift><Control><Alt>Tab
s0_next_group_button = Disabled
s0_next_group_key = Disabled
s0_prev_group_button = Disabled
s0_prev_group_key = Disabled
s0_next_no_popup_button = Disabled
s0_next_no_popup_key = Disabled
s0_prev_no_popup_button = Disabled
s0_prev_no_popup_key = Disabled
s0_next_panel_button = Disabled
s0_next_panel_key = Disabled
s0_prev_panel_button = Disabled
s0_prev_panel_key = Disabled
s0_speed = 4.000000
s0_timestep = 1.200000
s0_window_match = Normal | Dialog | Toolbar | Utility | Unknown
s0_minimized = true
s0_auto_change_vp = true
s0_popup_delay = 0.200000
s0_mouse_select = true
s0_saturation = 100
s0_brightness = 100
s0_opacity = 100
s0_icon = true
s0_icon_only = false
s0_mipmap = false
s0_row_align = 1
s0_focus_on_switch = false
s0_bring_to_front = false
s0_highlight_mode = 0
s0_highlight_rect_hidden = 1
s0_highlight_color = #00000096
s0_highlight_border_color = #000000c8
s0_highlight_border_inlay_color = #c8c8c8c8

[session]
s0_save_legacy = false
s0_ignore_match = 

[scalefilter]
s0_timeout = 0
s0_filter_case_insensitive = true
s0_filter_display = true
s0_font_bold = true
s0_font_size = 24
s0_border_size = 5
s0_font_color = #ffffffff
s0_back_color = #00000099

[fadedesktop]
s0_fadetime = 500
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown

[wall]
s0_show_switcher = true
s0_miniscreen = true
s0_preview_timeout = 0.200000
s0_preview_scale = 130
s0_edge_radius = 5
s0_border_width = 7
s0_outline_color = #ffffff32
s0_background_gradient_base_color = #00000064
s0_background_gradient_highlight_color = #00000064
s0_background_gradient_shadow_color = #00000064
s0_thumb_gradient_base_color = #55555532
s0_thumb_gradient_highlight_color = #55555532
s0_thumb_highlight_gradient_base_color = #ffffffff
s0_thumb_highlight_gradient_shadow_color = #dfdfdfff
s0_arrow_base_color = #e6e6e6d9
s0_arrow_shadow_color = #dcdcdcd9
s0_allow_wraparound = false
s0_slide_duration = 0.300000
s0_no_slide_match = 
s0_left_key = <Control><Alt>Left
s0_left_button = Disabled
s0_right_key = <Control><Alt>Right
s0_right_button = Disabled
s0_up_key = <Control><Alt>Up
s0_up_button = Disabled
s0_down_key = <Control><Alt>Down
s0_down_button = Disabled
s0_next_key = Disabled
s0_next_button = Disabled
s0_prev_key = Disabled
s0_prev_button = Disabled
s0_left_window_key = <Shift><Control><Alt>Left
s0_right_window_key = <Shift><Control><Alt>Right
s0_up_window_key = <Shift><Control><Alt>Up
s0_down_window_key = <Shift><Control><Alt>Down
s0_flip_left_edge = Left
s0_flip_right_edge = Right
s0_flip_up_edge = Top
s0_flip_down_edge = Bottom
s0_mmmode = 0
s0_edgeflip_pointer = false
s0_edgeflip_move = false
s0_edgeflip_dnd = false

[bench]
s0_initiate_key = <Super>F12
s0_fps_limiter_mode = 0
s0_output_screen = true
s0_position_x = 0
s0_position_y = 0
s0_output_console = false
s0_console_update_time = 5

[titleinfo]
s0_show_remote_machine = true
s0_show_root = true

[mblur]
s0_initiate_key = <Control>F12
s0_mode = 0
s0_strength = 20.000000
s0_on_transformed_screen = false

[commands]
s0_command0 = 
s0_command1 = 
s0_command2 = 
s0_command3 = 
s0_command4 = 
s0_command5 = 
s0_command6 = 
s0_command7 = 
s0_command8 = 
s0_command9 = 
s0_command10 = 
s0_command11 = 
s0_command12 = 
s0_command13 = 
s0_command14 = 
s0_command15 = 
s0_command16 = 
s0_command17 = 
s0_command18 = 
s0_command19 = 
s0_command20 = 
s0_run_command0_key = Disabled
s0_run_command1_key = Disabled
s0_run_command2_key = Disabled
s0_run_command3_key = Disabled
s0_run_command4_key = Disabled
s0_run_command5_key = Disabled
s0_run_command6_key = Disabled
s0_run_command7_key = Disabled
s0_run_command8_key = Disabled
s0_run_command9_key = Disabled
s0_run_command10_key = Disabled
s0_run_command11_key = Disabled
s0_run_command12_key = Disabled
s0_run_command13_key = Disabled
s0_run_command14_key = Disabled
s0_run_command15_key = Disabled
s0_run_command16_key = Disabled
s0_run_command17_key = Disabled
s0_run_command18_key = Disabled
s0_run_command19_key = Disabled
s0_run_command20_key = Disabled
s0_run_command0_button = Disabled
s0_run_command1_button = Disabled
s0_run_command2_button = Disabled
s0_run_command3_button = Disabled
s0_run_command4_button = Disabled
s0_run_command5_button = Disabled
s0_run_command6_button = Disabled
s0_run_command7_button = Disabled
s0_run_command8_button = Disabled
s0_run_command9_button = Disabled
s0_run_command10_button = Disabled
s0_run_command11_button = Disabled
s0_run_command12_button = Disabled
s0_run_command13_button = Disabled
s0_run_command14_button = Disabled
s0_run_command15_button = Disabled
s0_run_command16_button = Disabled
s0_run_command17_button = Disabled
s0_run_command18_button = Disabled
s0_run_command19_button = Disabled
s0_run_command20_button = Disabled
s0_run_command0_edge = 
s0_run_command1_edge = 
s0_run_command2_edge = 
s0_run_command3_edge = 
s0_run_command4_edge = 
s0_run_command5_edge = 
s0_run_command6_edge = 
s0_run_command7_edge = 
s0_run_command8_edge = 
s0_run_command9_edge = 
s0_run_command10_edge = 
s0_run_command11_edge = 
s0_run_command12_edge = 
s0_run_command13_edge = 
s0_run_command14_edge = 
s0_run_command15_edge = 
s0_run_command16_edge = 
s0_run_command17_edge = 
s0_run_command18_edge = 
s0_run_command19_edge = 
s0_run_command20_edge = 

[core]
s0_active_plugins = core;bailer;detection;composite;opengl;compiztoolbox;decor;regex;ring;animation;move;imgjpeg;gnomecompat;grid;imgpng;vpswitch;resize;place;workarounds;wobbly;mousepoll;animationaddon;session;thumbnail;ezoom;fade;addhelper;cube;rotate;
s0_audible_bell = true
s0_ignore_hints_when_maximized = true
s0_hide_skip_taskbar_windows = true
s0_edge_delay = 0
s0_ping_delay = 5000
s0_default_icon = icon
s0_do_serialize = false
s0_overlapping_outputs = 0
s0_detect_outputs = true
s0_outputs = 640x480+0+0;
s0_click_to_focus = true
s0_raise_on_click = true
s0_autoraise = true
s0_autoraise_delay = 1000
s0_focus_prevention_level = 1
s0_focus_prevention_match = !(class=Polkit-gnome-authentication-agent-1)
s0_close_window_key = <Alt>F4
s0_close_window_button = Disabled
s0_raise_window_key = Disabled
s0_raise_window_button = <Control>Button6
s0_lower_window_key = Disabled
s0_lower_window_button = <Alt>Button6
s0_minimize_window_key = <Alt>F9
s0_minimize_window_button = Disabled
s0_maximize_window_key = <Alt>F10
s0_unmaximize_window_key = <Alt>F5
s0_maximize_window_horizontally_key = Disabled
s0_maximize_window_vertically_key = Disabled
s0_window_menu_key = <Alt>space
s0_window_menu_button = <Alt>Button3
s0_show_desktop_key = <Control><Alt>d
s0_show_desktop_edge = 
s0_toggle_window_maximized_key = Disabled
s0_toggle_window_maximized_button = Disabled
s0_toggle_window_maximized_horizontally_key = Disabled
s0_toggle_window_maximized_vertically_key = Disabled
s0_toggle_window_shaded_key = <Control><Alt>s
s0_hsize = 4
s0_vsize = 1
s0_number_of_desktops = 1

[bailer]
s0_fatal_fallback_mode = 2
s0_custom_fallback_window_manager = 
s0_custom_alternative_shell = 
s0_poor_performance_fallback = 0
s0_bad_performance_threshold = 50
s0_bad_plugins = 

[trailfocus]
s0_window_match = (type=toolbar | type=utility | type=dialog | type=normal) & !(state=skiptaskbar | state=skippager)
s0_windows_count = 5
s0_windows_start = 2
s0_max_opacity = 100
s0_min_opacity = 70
s0_max_brightness = 100
s0_min_brightness = 100
s0_max_saturation = 100
s0_min_saturation = 100

[maximumize]
s0_ignore_sticky = true
s0_ignore_overlapping = false
s0_allow_shrink = true
s0_maximumize_left = true
s0_maximumize_right = true
s0_maximumize_up = true
s0_maximumize_down = true
s0_trigger_max_key = <Super>M
s0_trigger_max_left = Disabled
s0_trigger_max_right = Disabled
s0_trigger_max_up = Disabled
s0_trigger_max_down = Disabled
s0_trigger_max_horizontally = Disabled
s0_trigger_max_vertically = Disabled
s0_trigger_max_up_left = Disabled
s0_trigger_max_up_right = Disabled
s0_trigger_max_down_left = Disabled
s0_trigger_max_down_right = Disabled
s0_trigger_min_key = <Shift><Super>M
s0_trigger_min_left = Disabled
s0_trigger_min_right = Disabled
s0_trigger_min_up = Disabled
s0_trigger_min_down = Disabled
s0_trigger_min_horizontally = Disabled
s0_trigger_min_vertically = Disabled
s0_trigger_min_up_left = Disabled
s0_trigger_min_up_right = Disabled
s0_trigger_min_down_left = Disabled
s0_trigger_min_down_right = Disabled

[notification]
s0_timeout = -1
s0_max_log_level = 1

[water]
s0_initiate_key = <Control><Super>
s0_toggle_rain_key = <Shift>F9
s0_toggle_wiper_key = <Shift>F8
s0_offset_scale = 1.000000
s0_rain_delay = 250
s0_title_wave = false

[vpswitch]
s0_begin_key = Disabled
s0_switch_to_1_key = Disabled
s0_switch_to_2_key = Disabled
s0_switch_to_3_key = Disabled
s0_switch_to_4_key = Disabled
s0_switch_to_5_key = Disabled
s0_switch_to_6_key = Disabled
s0_switch_to_7_key = Disabled
s0_switch_to_8_key = Disabled
s0_switch_to_9_key = Disabled
s0_switch_to_10_key = Disabled
s0_switch_to_11_key = Disabled
s0_switch_to_12_key = Disabled
s0_left_button = Disabled
s0_right_button = Disabled
s0_up_button = Disabled
s0_down_button = Disabled
s0_next_button = Disabled
s0_prev_button = Disabled
s0_initiate_button = Button2
s0_init_plugin = rotate
s0_init_action = initiate_button

[group]
s0_select_button = Disabled
s0_select_single_key = <Super>s
s0_group_key = <Super>g
s0_ungroup_key = <Super>u
s0_remove_key = <Super>r
s0_close_key = <Super>c
s0_ignore_key = <Super>x
s0_tabmode_key = <Super>t
s0_change_tab_left_key = <Super>Left
s0_change_tab_right_key = <Super>Right
s0_change_color_key = Disabled
s0_move_all = true
s0_resize_all = false
s0_raise_all = true
s0_maximize_unmaximize_all = false
s0_minimize_all = true
s0_shade_all = false
s0_auto_group = false
s0_auto_ungroup = true
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_select_opacity = 80
s0_select_saturation = 20
s0_select_brightness = 70
s0_select_precision = 25
s0_fill_color = #00000055
s0_line_color = #000000ab
s0_mipmaps = false
s0_untab_on_close = false
s0_autotab_create = false
s0_autotab_windows = 
s0_tabbar_show_delay = 0.400000
s0_tabbing_speed = 1.200000
s0_tabbing_timestep = 1.500000
s0_fade_time = 0.200000
s0_pulse_time = 0.600000
s0_reflex_time = 0.500000
s0_fade_text_time = 0.250000
s0_visibility_time = 0.500000
s0_change_animation_time = 0.500000
s0_bar_animations = true
s0_thumb_size = 96
s0_thumb_space = 5
s0_border_radius = 10
s0_border_width = 1
s0_tab_base_color = #00000099
s0_tab_border_color = #000000ab
s0_tab_highlight_color = #ffffff99
s0_tab_style = 0
s0_tabbar_font_size = 12
s0_tabbar_font_color = #ffffffff
s0_dnd_ungroup_window = true
s0_drag_hover_time = 0.500000
s0_drag_spring_k = 8.000000
s0_drag_friction = 35.000000
s0_drag_y_distance = 400
s0_drag_speed_limit = 800
s0_glow = true
s0_glow_size = 64
s0_glow_type = 0

[opacify]
s0_toggle_key = <Super>o
s0_toggle_reset = true
s0_timeout = 700
s0_init_toggle = true
s0_only_if_block = false
s0_focus_instant = false
s0_no_delay_change = false
s0_window_match = Normal | Dialog | ModalDialog | Utility | Toolbar | Fullscreen
s0_active_opacity = 100
s0_passive_opacity = 10

[kdecompat]
s0_plasma_thumbnails = true
s0_present_windows = true
s0_window_blur = true
s0_sliding_popups = true
s0_slide_in_duration = 250
s0_slide_out_duration = 250

[thumbnail]
s0_thumb_size = 200
s0_show_delay = 100
s0_border = 16
s0_thumb_color = #0000007f
s0_fade_speed = 0.500000
s0_current_viewport = true
s0_always_on_top = true
s0_window_like = true
s0_mipmap = false
s0_title_enabled = true
s0_font_bold = true
s0_font_size = 12
s0_font_color = #000000ff

[resize]
s0_outline_modifier = 
s0_rectangle_modifier = 
s0_stretch_modifier = 
s0_centered_modifier = 0;
s0_initiate_button = <Alt>Button2
s0_initiate_key = <Alt>F8
s0_mode = 2
s0_border_color = #aafb009f
s0_fill_color = #b5fb0019
s0_normal_match = 
s0_outline_match = 
s0_rectangle_match = 
s0_stretch_match = 
s0_resize_from_center_match = 

[crashhandler]
s0_enabled = true
s0_directory = /tmp
s0_start_wm = false
s0_wm_cmd = 

[resizeinfo]
s0_fade_time = 500
s0_always_show = false
s0_text_color = #000000ff
s0_gradient_1 = #cccce6cc
s0_gradient_2 = #f3f3f3cc
s0_gradient_3 = #d9d9d9cc

[cubeaddon]
s0_top_next_key = space
s0_top_next_button = Disabled
s0_top_prev_key = Disabled
s0_top_prev_button = Disabled
s0_bottom_next_key = Disabled
s0_bottom_next_button = Disabled
s0_bottom_prev_key = Disabled
s0_bottom_prev_button = Disabled
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_intensity = 0.400000
s0_auto_zoom = true
s0_zoom_manual_only = true
s0_mode = 0
s0_deformation = 1
s0_unfold_deformation = true
s0_cylinder_manual_only = false
s0_deform_caps = true
s0_sphere_aspect = 0.000000
s0_draw_top = true
s0_draw_bottom = true
s0_adjust_top = false
s0_adjust_bottom = false
s0_top_scale = true
s0_bottom_scale = true
s0_top_aspect = true
s0_bottom_aspect = true
s0_top_clamp = true
s0_bottom_clamp = true
s0_top_images = fusioncap.png;
s0_bottom_images = compizcap.png;

[place]
s0_workarounds = true
s0_mode = 2
s0_multioutput_mode = 0
s0_force_placement_match = 
s0_position_matches = 
s0_position_x_values = 
s0_position_y_values = 
s0_position_constrain_workarea = 
s0_mode_matches = 
s0_mode_modes = 
s0_viewport_matches = 
s0_viewport_x_values = 
s0_viewport_y_values = 

[cube]
s0_unfold_key = <Control><Alt>Down
s0_mipmap = true
s0_multioutput_mode = 1
s0_in = false
s0_acceleration = 4.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_top_color = #cdbe70ff
s0_bottom_color = #cdbe70ff
s0_skydome = false
s0_skydome_image = /home/silver/Downloads/133507-1.jpg
s0_skydome_animated = false
s0_skydome_gradient_start_color = #0db1fdff
s0_skydome_gradient_end_color = #feffc7ff
s0_active_opacity = 100.000000
s0_inactive_opacity = 100.000000
s0_transparent_manual_only = true

[put]
s0_put_viewport_1_key = Disabled
s0_put_viewport_2_key = Disabled
s0_put_viewport_3_key = Disabled
s0_put_viewport_4_key = Disabled
s0_put_viewport_5_key = Disabled
s0_put_viewport_6_key = Disabled
s0_put_viewport_7_key = Disabled
s0_put_viewport_8_key = Disabled
s0_put_viewport_9_key = Disabled
s0_put_viewport_10_key = Disabled
s0_put_viewport_11_key = Disabled
s0_put_viewport_12_key = Disabled
s0_put_viewport_left_key = Disabled
s0_put_viewport_right_key = Disabled
s0_put_viewport_up_key = Disabled
s0_put_viewport_down_key = Disabled
s0_put_center_key = <Super>KP_Begin
s0_put_center_button = Disabled
s0_put_left_key = <Super>KP_Left
s0_put_left_button = Disabled
s0_put_right_key = <Super>KP_Right
s0_put_right_button = Disabled
s0_put_top_key = <Super>KP_Up
s0_put_top_button = Disabled
s0_put_bottom_key = <Super>KP_Down
s0_put_bottom_button = Disabled
s0_put_topleft_key = <Super>KP_Home
s0_put_topleft_button = Disabled
s0_put_topright_key = <Super>KP_Prior
s0_put_topright_button = Disabled
s0_put_bottomleft_key = <Super>KP_End
s0_put_bottomleft_button = Disabled
s0_put_bottomright_key = <Super>KP_Next
s0_put_bottomright_button = Disabled
s0_put_empty_center_key = Disabled
s0_put_empty_center_button = Disabled
s0_put_empty_left_key = Disabled
s0_put_empty_left_button = Disabled
s0_put_empty_right_key = Disabled
s0_put_empty_right_button = Disabled
s0_put_empty_top_key = Disabled
s0_put_empty_top_button = Disabled
s0_put_empty_bottom_key = Disabled
s0_put_empty_bottom_button = Disabled
s0_put_empty_topleft_key = Disabled
s0_put_empty_topleft_button = Disabled
s0_put_empty_topright_key = Disabled
s0_put_empty_topright_button = Disabled
s0_put_empty_bottomleft_key = Disabled
s0_put_empty_bottomleft_button = Disabled
s0_put_empty_bottomright_key = Disabled
s0_put_empty_bottomright_button = Disabled
s0_put_restore_key = <Super>KP_Insert
s0_put_restore_button = Disabled
s0_put_pointer_key = <Super>z
s0_put_pointer_button = Disabled
s0_put_next_output_key = Disabled
s0_put_next_output_button = Disabled
s0_pad_left = 0
s0_pad_right = 0
s0_pad_top = 0
s0_pad_bottom = 0
s0_unfocus_window = false
s0_window_center = false
s0_avoid_offscreen = false
s0_speed = 2.500000
s0_timestep = 0.500000

[ezoom]
s0_zoom_in_button = Disabled
s0_zoom_in_key = Disabled
s0_zoom_out_button = Disabled
s0_zoom_out_key = Disabled
s0_zoom_box_button = Disabled
s0_center_mouse_key = Disabled
s0_zoom_specific_1_key = Disabled
s0_zoom_spec1 = 1.000000
s0_zoom_specific_2_key = Disabled
s0_zoom_spec2 = 0.500000
s0_zoom_specific_3_key = Disabled
s0_zoom_spec3 = 0.200000
s0_spec_target_focus = true
s0_lock_zoom_key = Disabled
s0_pan_left_key = Disabled
s0_pan_right_key = Disabled
s0_pan_up_key = Disabled
s0_pan_down_key = Disabled
s0_fit_to_zoom_key = Disabled
s0_fit_to_window_key = Disabled
s0_zoom_factor = 1.150000
s0_minimum_zoom = 0.125000
s0_zoom_mode = 0
s0_scale_mouse = true
s0_scale_mouse_dynamic = true
s0_scale_mouse_static = 0.200000
s0_hide_original_mouse = true
s0_restrain_mouse = false
s0_restrain_margin = 5
s0_pan_factor = 0.100000
s0_follow_focus = true
s0_focus_fit_window = false
s0_autoscale_min = 0.250000
s0_always_focus_fit_window = false
s0_follow_focus_delay = 0
s0_speed = 25.000000
s0_timestep = 1.200000

[fade]
s0_fade_mode = 0
s0_fade_speed = 5.000000
s0_fade_time = 100
s0_window_match = any & !(title=notify-osd)
s0_visual_bell = false
s0_fullscreen_visual_bell = false
s0_dim_unresponsive = true
s0_unresponsive_brightness = 65
s0_unresponsive_saturation = 0

[obs]
s0_opacity_increase_key = Disabled
s0_opacity_increase_button = <Alt>Button4
s0_opacity_decrease_key = Disabled
s0_opacity_decrease_button = <Alt>Button5
s0_opacity_step = 5
s0_opacity_matches = 
s0_opacity_values = 
s0_brightness_increase_key = Disabled
s0_brightness_increase_button = Disabled
s0_brightness_decrease_key = Disabled
s0_brightness_decrease_button = Disabled
s0_brightness_step = 5
s0_brightness_matches = 
s0_brightness_values = 
s0_saturation_increase_key = Disabled
s0_saturation_increase_button = Disabled
s0_saturation_decrease_key = Disabled
s0_saturation_decrease_button = Disabled
s0_saturation_step = 5
s0_saturation_matches = 
s0_saturation_values = 

[workarounds]
s0_keep_minimized_windows = false
s0_legacy_fullscreen = false
s0_firefox_menu_fix = false
s0_ooo_menu_fix = true
s0_notification_daemon_fix = false
s0_java_fix = true
s0_java_taskbar_fix = true
s0_qt_fix = false
s0_convert_urgency = false
s0_aiglx_fragment_fix = true
s0_fglrx_xgl_fix = false
s0_force_glx_sync = false
s0_no_wait_for_video_sync = false
s0_force_swap_buffers = false
s0_sticky_alldesktops = false
s0_alldesktop_sticky_match = any

[addhelper]
s0_toggle_key = <Super>p
s0_window_types = Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal
s0_ononinit = false
s0_brightness = 30
s0_saturation = 50
s0_opacity = 100

[showdesktop]
s0_speed = 1.200000
s0_timestep = 0.100000
s0_direction = 6
s0_window_match = type=toolbar | type=utility | type=dialog | type=normal
s0_window_opacity = 0.300000
s0_window_part_size = 20

[snap]
s0_avoid_snap = 0;
s0_snap_type = 0;
s0_edges_categories = 0;
s0_resistance_distance = 30
s0_attraction_distance = 20

[colorfilter]
s0_toggle_window_key = <Super>f
s0_toggle_screen_key = <Super>d
s0_switch_filter_key = <Control><Super>s
s0_filters = negative;negative-green;blueish-filter;sepia;grayscale;deuteranopia;protanopia;
s0_filter_decorations = false
s0_filter_match = any
s0_exclude_match = type=Desktop

[shelf]
s0_trigger_key = <Super>l
s0_reset_key = Disabled
s0_triggerscreen_key = <Super>p
s0_dec_button = <Alt><Super>Button4
s0_inc_button = <Alt><Super>Button5
s0_animtime = 150
s0_interval = 0.900000

[scaleaddon]
s0_close_key = Disabled
s0_close_button = Button2
s0_pull_key = Disabled
s0_pull_button = Disabled
s0_zoom_key = Disabled
s0_zoom_button = Button3
s0_window_title = 1
s0_title_bold = false
s0_title_size = 13
s0_border_size = 3
s0_font_color = #ffffffff
s0_back_color = #00000099
s0_window_highlight = false
s0_highlight_color = #ffffff96
s0_layout_mode = 0
s0_natural_precision = 2.000000
s0_constrain_pull_to_screen = true
s0_exit_after_pull = false

[zoom]
s0_initiate_button = <Super>Button3
s0_zoom_in_button = <Super>Button4
s0_zoom_out_button = <Super>Button5
s0_zoom_pan_button = <Super>Button2
s0_speed = 1.500000
s0_timestep = 1.200000
s0_zoom_factor = 2.000000
s0_filter_linear = false

[showmouse]
s0_initiate = <Super>k
s0_initiate_button = Disabled
s0_initiate_edge = 
s0_num_particles = 500
s0_size = 10.000000
s0_slowdown = 1.000000
s0_life = 0.700000
s0_darken = 0.900000
s0_blend = true
s0_color = #ffdf3fff
s0_random = false
s0_rotation_speed = 0.500000
s0_radius = 100
s0_emiters = 3

[shift]
s0_initiate_key = <Shift><Super>s
s0_initiate_button = Disabled
s0_initiate_edge = 
s0_initiate_all_key = Disabled
s0_initiate_all_button = Disabled
s0_initiate_all_edge = 
s0_terminate_button = Button3
s0_next_key = <Super>Tab
s0_next_button = Disabled
s0_prev_key = <Shift><Super>Tab
s0_prev_button = Disabled
s0_next_all_key = <Alt><Super>Tab
s0_next_all_button = Disabled
s0_prev_all_key = <Shift><Alt><Super>Tab
s0_prev_all_button = Disabled
s0_next_group_key = Disabled
s0_next_group_button = Disabled
s0_prev_group_key = Disabled
s0_prev_group_button = Disabled
s0_speed = 1.500000
s0_shift_speed = 1.000000
s0_timestep = 1.200000
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_minimized = true
s0_mouse_speed = 10.000000
s0_click_duration = 500
s0_mode = 0
s0_size = 50
s0_background_intensity = 0.500000
s0_hide_all = false
s0_reflection = true
s0_ground_color1 = #b3b3b3cc
s0_ground_color2 = #b3b3b300
s0_ground_size = 0.500000
s0_intensity = 0.400000
s0_flip_rotation = 30
s0_cover_offset = 0.000000
s0_cover_angle = 60.000000
s0_cover_extra_space = 1.000000
s0_cover_max_visible_windows = 10
s0_overlay_icon = 1
s0_mipmaps = false
s0_multioutput_mode = 0
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 2

[scale]
s0_spacing = 68
s0_speed = 2.400000
s0_timestep = 0.100000
s0_darken_back = true
s0_opacity = 100
s0_overlay_icon = 0
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_hover_time = 750
s0_multioutput_mode = 0
s0_key_bindings_toggle = true
s0_button_bindings_toggle = false
s0_initiate_edge = 
s0_initiate_key = <Shift><Alt>Up
s0_initiate_button = Disabled
s0_initiate_all_edge = 
s0_initiate_all_button = Disabled
s0_initiate_all_key = <Super>w
s0_initiate_group_edge = 
s0_initiate_group_button = Disabled
s0_initiate_group_key = Disabled
s0_initiate_output_edge = 
s0_initiate_output_button = Disabled
s0_initiate_output_key = Disabled
s0_show_desktop = false

[opengl]
s0_texture_filter = 1
s0_lighting = false
s0_sync_to_vblank = true
s0_texture_compression = false

[screenshot]
s0_initiate_button = <Super>Button1
s0_directory = 
s0_launch_app = 

[wobbly]
s0_snap_key = <Shift>
s0_snap_inverted = false
s0_shiver = false
s0_friction = 3.000000
s0_spring_k = 8.000000
s0_grid_resolution = 8
s0_min_grid_size = 8
s0_map_effect = 0
s0_focus_effect = 0
s0_map_window_match = Splash | DropdownMenu | PopupMenu | Tooltip | Notification | Combo | Dnd | Unknown
s0_focus_window_match = 
s0_grab_window_match = 
s0_move_window_match = Toolbar | Menu | Utility | Dialog | Normal | Unknown
s0_maximize_effect = true

[mousepoll]
s0_mouse_poll_interval = 40

[debugspew]
s0_spew_key = Disabled
s0_spew_on_fatal = true

[widget]
s0_toggle_key = F9
s0_toggle_button = Disabled
s0_toggle_edge = 
s0_match = 
s0_end_on_click = true
s0_fade_time = 0.500000
s0_bg_brightness = 50
s0_bg_saturation = 100

[td]
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_min_cube_size = 60
s0_max_window_space = 10
s0_manual_only = false
s0_width = 0.300000
s0_bevel = 0
s0_width_color = #333333ff
s0_width_color_inactive = #333333ff
s0_bevel_topleft = true
s0_bevel_topright = true
s0_bevel_bottomleft = false
s0_bevel_bottomright = false

[splash]
s0_initiate_key = <Control>F11
s0_firststart = true
s0_background = splash_background.png
s0_logo = splash_logo.png
s0_fade_time = 1.000000
s0_display_time = 2.000000
s0_saturation = 50.000000
s0_brightness = 50.000000

[rotate]
s0_edge_flip_pointer = false
s0_edge_flip_window = true
s0_edge_flip_dnd = true
s0_raise_on_rotate = true
s0_invert_y = false
s0_snap_top = true
s0_snap_bottom = false
s0_zoom = 0.430300
s0_flip_time = 350
s0_sensitivity = 1.000000
s0_acceleration = 4.000000
s0_speed = 2.000000
s0_timestep = 1.000000
s0_initiate_button = <Control><Alt>Button1
s0_rotate_left_key = <Control><Alt>Left
s0_rotate_left_button = Disabled
s0_rotate_right_key = <Control><Alt>Right
s0_rotate_right_button = Disabled
s0_rotate_left_window_key = <Shift><Control><Alt>Left
s0_rotate_left_window_button = Disabled
s0_rotate_right_window_key = <Shift><Control><Alt>Right
s0_rotate_right_window_button = Disabled
s0_rotate_to_key = Disabled
s0_rotate_window_key = Disabled
s0_rotate_flip_left_edge = Left
s0_rotate_flip_right_edge = Right
s0_rotate_to_1_key = Disabled
s0_rotate_to_2_key = Disabled
s0_rotate_to_3_key = Disabled
s0_rotate_to_4_key = Disabled
s0_rotate_to_5_key = Disabled
s0_rotate_to_6_key = Disabled
s0_rotate_to_7_key = Disabled
s0_rotate_to_8_key = Disabled
s0_rotate_to_9_key = Disabled
s0_rotate_to_10_key = Disabled
s0_rotate_to_11_key = Disabled
s0_rotate_to_12_key = Disabled
s0_rotate_to_1_window_key = Disabled
s0_rotate_to_2_window_key = Disabled
s0_rotate_to_3_window_key = Disabled
s0_rotate_to_4_window_key = Disabled
s0_rotate_to_5_window_key = Disabled
s0_rotate_to_6_window_key = Disabled
s0_rotate_to_7_window_key = Disabled
s0_rotate_to_8_window_key = Disabled
s0_rotate_to_9_window_key = Disabled
s0_rotate_to_10_window_key = Disabled
s0_rotate_to_11_window_key = Disabled
s0_rotate_to_12_window_key = Disabled

[blur]
s0_pulse = false
s0_blur_speed = 3.500000
s0_focus_blur_match = toolbar | menu | utility | normal | dialog | modaldialog
s0_focus_blur = false
s0_alpha_blur_match = 
s0_alpha_blur = true
s0_filter = 0
s0_gaussian_radius = 3
s0_gaussian_strength = 1.000000
s0_mipmap_lod = 2.500000
s0_saturation = 100
s0_occlusion = true
s0_independent_tex = false

[mag]
s0_initiate = <Super>m
s0_zoom_in_button = <Shift><Super>Button4
s0_zoom_out_button = <Shift><Super>Button5
s0_mode = 0
s0_zoom_factor = 2.000000
s0_speed = 1.500000
s0_timestep = 1.200000
s0_keep_screen = true
s0_box_width = 300
s0_box_height = 200
s0_border = 2
s0_box_color = #000000ff
s0_overlay = Gnome/overlay.png
s0_mask = Gnome/mask.png
s0_x_offset = 155
s0_y_offset = 155
s0_radius = 200

[neg]
s0_window_toggle_key = <Super>n
s0_screen_toggle_key = <Super>m
s0_neg_match = any
s0_exclude_match = type=Desktop
s0_neg_decorations = false

[loginout]
s0_in_match = (iclass=^ksplash)
s0_in_time = 1.000000
s0_in_saturation = 0.000000
s0_in_brightness = 100.000000
s0_in_opacity = 100.000000
s0_out_match = (iclass=ksmserver & (role=logoutdialog | role=logouteffect)) | (class=Libssui-tool & type=Dialog)
s0_out_time = 1.000000
s0_out_saturation = 0.000000
s0_out_brightness = 100.000000
s0_out_opacity = 100.000000

[decor]
s0_shadow_radius = 15.000000
s0_shadow_opacity = 0.500000
s0_shadow_color = #00000000
s0_shadow_x_offset = 1
s0_shadow_y_offset = 5
s0_command = gtk-window-decorator --replace
s0_mipmap = false
s0_decoration_match = any
s0_shadow_match = any

[animationaddon]
s0_time_step_intense = 30
s0_airplane_path_length = 1.000000
s0_airplane_fly_to_taskbar = true
s0_beam_size = 8.000000
s0_beam_spacing = 5
s0_beam_color = #7f7f7fff
s0_beam_slowdown = 1.000000
s0_beam_life = 0.700000
s0_fire_particles = 1000
s0_fire_size = 5.000000
s0_fire_slowdown = 0.500000
s0_fire_life = 0.700000
s0_fire_color = #ff3305ff
s0_fire_direction = 0
s0_fire_constant_speed = false
s0_fire_smoke = false
s0_fire_mystical = false
s0_domino_direction = 5
s0_explode_gridx = 13
s0_explode_gridy = 10
s0_explode_spokes = 2
s0_explode_tiers = 3
s0_explode_thickness = 15.000000
s0_explode_tessellation = 0
s0_fold_gridx = 3
s0_fold_gridy = 3
s0_fold_dir = 1
s0_glide3_away_position = -0.400000
s0_glide3_away_angle = 45.000000
s0_glide3_thickness = 0.000000
s0_razr_direction = 5
s0_skewer_direction = 8
s0_skewer_tessellation = 0
s0_skewer_gridx = 6
s0_skewer_gridy = 4
s0_skewer_thickness = 0.000000
s0_skewer_rotation = 0

[firepaint]
s0_initiate_key = Disabled
s0_initiate_button = <Shift><Super>Button1
s0_clear_key = <Shift><Super>c
s0_clear_button = Disabled
s0_num_particles = 3000
s0_fire_size = 15.000000
s0_fire_slowdown = 0.500000
s0_fire_life = 0.700000
s0_fire_color = #ff3305ff
s0_fire_mystical = false
s0_bg_brightness = 50

[extrawm]
s0_toggle_redirect_key = Disabled
s0_toggle_fullscreen_key = Disabled
s0_toggle_always_on_top_key = Disabled
s0_toggle_sticky_key = Disabled
s0_activate_demands_attention_key = Disabled

[annotate]
s0_initiate_free_draw_button = <Alt><Super>Button1
s0_initiate_line_button = <Alt><Super>Button2
s0_initiate_rectangle_button = <Shift><Alt><Super>Button1
s0_initiate_ellipse_button = <Shift><Alt><Super>Button2
s0_erase_button = <Alt><Super>Button3
s0_clear_key = <Alt><Super>k
s0_clear_button = Disabled
s0_draw_shapes_from_center = true
s0_fill_color = #ff000088
s0_stroke_color = #00ff00ff
s0_erase_width = 20.000000
s0_stroke_width = 3.000000

[ring]
s0_next_key = <Super>Tab
s0_next_button = Disabled
s0_prev_key = <Shift><Super>Tab
s0_prev_button = Disabled
s0_next_all_key = <Alt><Super>Tab
s0_next_all_button = Disabled
s0_prev_all_key = <Shift><Alt><Super>Tab
s0_prev_all_button = Disabled
s0_next_group_key = Disabled
s0_next_group_button = Disabled
s0_prev_group_key = Disabled
s0_prev_group_button = Disabled
s0_speed = 1.500000
s0_timestep = 1.200000
s0_inactive_opacity = 100
s0_window_match = Normal | Dialog | ModalDialog | Utility | Unknown
s0_overlay_icon = 1
s0_darken_back = true
s0_minimized = true
s0_select_with_mouse = false
s0_ring_clockwise = false
s0_ring_width = 70
s0_ring_height = 60
s0_thumb_width = 350
s0_thumb_height = 250
s0_min_brightness = 0.500000
s0_min_scale = 0.400000
s0_window_title = true
s0_title_font_bold = false
s0_title_font_size = 16
s0_title_back_color = #00000099
s0_title_font_color = #ffffffff
s0_title_text_placement = 0

[switcher]
s0_next_button = Disabled
s0_next_key = <Alt>Tab
s0_prev_button = Disabled
s0_prev_key = <Shift><Alt>Tab
s0_next_all_button = Disabled
s0_next_all_key = <Control><Alt>Tab
s0_prev_all_button = Disabled
s0_prev_all_key = <Shift><Control><Alt>Tab
s0_next_no_popup_button = Disabled
s0_next_no_popup_key = Disabled
s0_prev_no_popup_button = Disabled
s0_prev_no_popup_key = Disabled
s0_next_panel_button = Disabled
s0_next_panel_key = Disabled
s0_prev_panel_button = Disabled
s0_prev_panel_key = Disabled
s0_speed = 1.500000
s0_timestep = 1.200000
s0_window_match = Toolbar | Utility | Dialog | Normal | Unknown
s0_mipmap = true
s0_saturation = 100
s0_brightness = 65
s0_opacity = 40
s0_focus_on_switch = false
s0_bring_to_front = true
s0_zoom = 1.000000
s0_icon = true
s0_icon_only = false
s0_minimized = true
s0_auto_rotate = false

[animation]
s0_open_effects = animation:Glide 2;animation:None;animation:Fade;
s0_open_durations = 120;80;80;
s0_open_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver);(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal);(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd);
s0_open_options = ;;;
s0_open_random_effects = 
s0_close_effects = animation:Glide2;animation:Fade;animation:None;
s0_close_durations = 120;80;50;
s0_close_matches = ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver) & !(name=gnome-screenshot);(type=Menu | PopupMenu | DropdownMenu | Combo | Dialog | ModalDialog | Normal);(type=Tooltip | Notification | Utility) & !(name=compiz) & !(title=notify-osd);
s0_close_options = ;;;
s0_close_random_effects = 
s0_minimize_effects = animation:Magic Lamp Wavy;
s0_minimize_durations = 1228;
s0_minimize_matches = ;
s0_minimize_options = ;
s0_minimize_random_effects = 
s0_shade_effects = animation:Roll Up;
s0_shade_durations = 300;
s0_shade_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown);
s0_shade_options = ;
s0_shade_random_effects = 
s0_focus_effects = animation:Fade;
s0_focus_durations = 150;
s0_focus_matches = (type=Normal | Dialog | ModalDialog | Utility | Unknown) & !(name=compiz);
s0_focus_options = ;
s0_all_random = false
s0_time_step = 16
s0_curved_fold_amp_mult = 1.000000
s0_curved_fold_zoom_to_taskbar = true
s0_dodge_mode = 1
s0_dodge_gap_ratio = 0.500000
s0_dream_zoom_to_taskbar = true
s0_glide1_away_position = 1.000000
s0_glide1_away_angle = 0.000000
s0_glide1_zoom_to_taskbar = false
s0_glide2_away_position = -0.100000
s0_glide2_away_angle = 0.000000
s0_glide2_zoom_to_taskbar = true
s0_horizontal_folds_amp_mult = 1.000000
s0_horizontal_folds_num_folds = 3
s0_horizontal_folds_zoom_to_taskbar = true
s0_magic_lamp_moving_end = true
s0_magic_lamp_grid_res = 100
s0_magic_lamp_open_start_width = 30
s0_magic_lamp_wavy_moving_end = true
s0_magic_lamp_wavy_grid_res = 100
s0_magic_lamp_wavy_max_waves = 3
s0_magic_lamp_wavy_amp_min = 200.000000
s0_magic_lamp_wavy_amp_max = 300.000000
s0_magic_lamp_wavy_open_start_width = 30
s0_rollup_fixed_interior = false
s0_sidekick_num_rotations = 0.500000
s0_sidekick_springiness = 0.000000
s0_sidekick_zoom_from_center = 0
s0_wave_width = 0.700000
s0_wave_amp_mult = 1.000000
s0_zoom_from_center = 0
s0_zoom_springiness = 0.080000

[composite]
s0_slow_animations_key = Disabled
s0_detect_refresh_rate = true
s0_refresh_rate = 50
s0_unredirect_fullscreen_windows = false
s0_force_independent_output_painting = false

[clone]
s0_initiate_button = <Shift><Super>Button1

```

---

