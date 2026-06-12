---
title: "driconf and hyperz"
date: 2015-03-21
forum: Apple Hardware Users
---

### Post by rican-linux on 2015-03-21
This section of the wiki has always bothered me

```
There are a lot of 'wonder' xorg.conf files knocking around the internet that claim to have the secret formula to fantastic 3d performance. I've only found two things that make a big difference. The first is to reduce the colour depth (for example put DefaultDepth 16 into the screen section), but I prefer a greater colour depth so I don't do this. The second is to turn on HyperZ. This isn't done in xorg.conf, but in a ".drirc" file in your home folder. Install Driconf from the software centre/synaptic so that you can turn it on using the applet. I have no idea what this actually does, only it makes the numbers go up in glxgears!
```

I have seen that I can get 3D to work if I set my DefaultDepth to 16, but I hate the sreen resoltuion. So I have always wondered how to enable HyperZ on my .drirc file. I could not see any way to do it in the app so I found out how to do it manually. Below is my .drirc file and yet after reboot I noticed that driconf shows hyperz as an "unknown" option. Has anyone ever got this to actually work?

```
rican-linux@ibookG4-UbuntuMATE:~$ cat .drirc 
<driconf>
    <device screen="0" driver="r300">
        <application name="Default">
            <option name="force_s3tc_enable" value="false" />
            <option name="pp_celshade" value="0" />
            **<option name="hyperz" value="true" />**
            <option name="pp_jimenezmlaa" value="0" />
            <option name="always_have_depth_buffer" value="false" />
            <option name="pp_jimenezmlaa_color" value="0" />
            <option name="allow_glsl_extension_directive_midshader" value="false" />
            <option name="force_glsl_extensions_warn" value="false" />
            <option name="pp_nored" value="0" />
            <option name="force_glsl_version" value="0" />
            <option name="disable_glsl_line_continuations" value="false" />
            <option name="disable_shader_bit_encoding" value="false" />
            <option name="disable_blend_func_extended" value="false" />
            <option name="pp_nogreen" value="0" />
            <option name="pp_noblue" value="0" />
        </application>
        <application name="Unigine Sanctuary" executable="Sanctuary">
            <option name="force_glsl_extensions_warn" value="true" />
            <option name="disable_blend_func_extended" value="true" />
        </application>
        <application name="Unigine Tropics" executable="Tropics">
            <option name="force_glsl_extensions_warn" value="true" />
            <option name="disable_blend_func_extended" value="true" />
        </application>
        <application name="Unigine Heaven (32-bit)" executable="heaven_x86">
            <option name="force_glsl_extensions_warn" value="true" />
            <option name="force_glsl_version" value="130" />
            <option name="disable_blend_func_extended" value="true" />
            <option name="allow_glsl_extension_directive_midshader" value="true" />
            <option name="disable_shader_bit_encoding" value="true" />
        </application>
        <application name="Unigine Heaven (64-bit)" executable="heaven_x64">
            <option name="force_glsl_extensions_warn" value="true" />
            <option name="force_glsl_version" value="130" />
            <option name="disable_blend_func_extended" value="true" />
            <option name="allow_glsl_extension_directive_midshader" value="true" />
            <option name="disable_shader_bit_encoding" value="true" />
        </application>
        <application name="Unigine Valley (32-bit)" executable="valley_x86">
            <option name="allow_glsl_extension_directive_midshader" value="true" />
        </application>
        <application name="Unigine Valley (64-bit)" executable="valley_x64">
            <option name="allow_glsl_extension_directive_midshader" value="true" />
        </application>
        <application name="Unigine OilRush (32-bit)" executable="OilRush_x86">
            <option name="disable_blend_func_extended" value="true" />
        </application>
        <application name="Unigine OilRush (64-bit)" executable="OilRush_x64">
            <option name="disable_blend_func_extended" value="true" />
        </application>
        <application name="Savage 2" executable="savage2.bin">
            <option name="disable_glsl_line_continuations" value="true" />
        </application>
        <application name="Topogun (32-bit)" executable="topogun32">
            <option name="always_have_depth_buffer" value="true" />
        </application>
        <application name="Topogun (64-bit)" executable="topogun64">
            <option name="always_have_depth_buffer" value="true" />
        </application>
        <application name="Dead Island" executable="DeadIslandGame">
            <option name="allow_glsl_extension_directive_midshader" value="true" />
        </application>
    </device>
</driconf>

```

[ATTACH=CONFIG]260803[/ATTACH]

---

### Post by luigiburdo on 2015-03-22
I was pretty sure the 16bit resolution will make 3d better working.... how i know this because the same issue was face by AmigaOS 3.9 in past with some video boards.... 24/32 bit was making system freeze or wrong colors.
This why i ask in past xeno if he had been try a 16 bit screen for check if the 3d gave right color -

---

### Post by rican-linux on 2015-03-22
On my iBook since it has a smaller screen it is not an issue. However on my PowerBook it makes a big difference.

---

