---
title: "Compiling Help"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by yuvlevental on 2007-06-27
I'm trying to compile soya3d 0.13.1 However, I get this very long error:

*(lots of text)*
_soya.c:112978: error: expected ‘}’ before ‘__pyx_f_5_soya_clear_events’
_soya.c:112979: error: expected ‘}’ before ‘__pyx_f_5_soya_get_mouse_rel_pos’
_soya.c:112980: error: expected ‘}’ before ‘__pyx_f_5_soya_get_renderer’
_soya.c:112981: error: expected ‘}’ before ‘__pyx_f_5_soya_check_error’
_soya.c:112982: error: expected ‘}’ before ‘__pyx_f_5_soya_set_root_widget’
_soya.c:112983: error: expected ‘}’ before ‘__pyx_f_5_soya_render’
_soya.c:112984: error: expected ‘}’ before ‘__pyx_f_5_soya_get_screen_width’
_soya.c:112985: error: expected ‘}’ before ‘__pyx_f_5_soya_get_screen_height’
_soya.c:112986: error: expected ‘}’ before ‘__pyx_f_5_soya_CapsuleMass’
_soya.c:112987: error: expected ‘}’ before ‘__pyx_f_5_soya_CylindricalMass’
_soya.c:112988: error: expected ‘}’ before ‘__pyx_f_5_soya_BoxedMass’
_soya.c:112989: error: expected ‘}’ before ‘__pyx_f_5_soya_SphericalMass’
_soya.c:112990: error: expected ‘}’ before ‘__pyx_f_5_soya_collide’
_soya.c:112991: error: expected ‘}’ before ‘__pyx_f_5_soya_open_image’
_soya.c:112992: error: expected ‘}’ before ‘__pyx_f_5_soya_image_from_pil’
_soya.c:112993: error: expected ‘}’ before ‘__pyx_f_5_soya_screenshot’
_soya.c:112994: error: expected ‘}’ before ‘__pyx_f_5_soya__set_particle_default_material’
_soya.c:112995: error: expected ‘}’ before ‘__pyx_f_5_soya__is_static_light’
_soya.c:112996: error: expected ‘}’ before ‘__pyx_f_5_soya__set_default_model_builder’
_soya.c:112997: error: expected ‘}’ before ‘__pyx_f_5_soya_load_raw_image’
_soya.c:112998: error: expected ‘}’ before ‘__pyx_f_5_soya_parse_cal3d_cfg_file’
_soya.c:112999: error: expected ‘}’ before ‘__pyx_f_5_soya_check_al_error’
_soya.c:113000: error: expected ‘}’ before ‘__pyx_f_5_soya_set_sound_volume’
_soya.c:113001: error: expected ‘}’ before ‘__pyx_f_5_soya_get_sound_volume’
_soya.c:113007: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘init_soya’
_soya.c:113008: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘init_soya’
_soya.c:115204: error: expected ‘)’ before ‘*’ token
_soya.c:115218: error: expected ‘)’ before ‘*’ token
_soya.c:115286: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_soya.c:115294: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_soya.c:115311: error: expected ‘)’ before ‘*’ token
_soya.c:115323: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_soya.c: In function ‘__Pyx_WriteUnraisable’:
_soya.c:115357: error: ‘PyObject’ undeclared (first use in this function)
_soya.c:115357: error: ‘old_exc’ undeclared (first use in this function)
_soya.c:115357: error: invalid operands to binary *
_soya.c:115357: error: ‘old_val’ undeclared (first use in this function)
_soya.c:115357: error: ‘old_tb’ undeclared (first use in this function)
_soya.c:115358: error: ‘ctx’ undeclared (first use in this function)
_soya.c:115358: error: invalid operands to binary *
_soya.c:115363: error: ‘Py_None’ undeclared (first use in this function)
_soya.c: At top level:
_soya.c:115367: error: expected ‘)’ before ‘*’ token
_soya.c:115429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_soya.c:115437: error: expected ‘)’ before ‘*’ token
_soya.c: In function ‘__Pyx_PrintNewline’:
_soya.c:115460: error: ‘PyObject’ undeclared (first use in this function)
_soya.c:115460: error: ‘f’ undeclared (first use in this function)
_soya.c:115460: error: invalid operands to binary *
_soya.c: In function ‘__Pyx_UnpackError’:
_soya.c:115471: error: ‘PyExc_ValueError’ undeclared (first use in this function)
_soya.c: At top level:
_soya.c:115474: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_soya.c:115483: error: expected ‘)’ before ‘*’ token
_soya.c:115494: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
_soya.c: In function ‘__Pyx_InternStrings’:
_soya.c:115525: error: ‘__Pyx_InternTabEntry’ has no member named ‘p’
_soya.c:115526: error: ‘__Pyx_InternTabEntry’ has no member named ‘p’
_soya.c:115526: error: ‘__Pyx_InternTabEntry’ has no member named ‘s’
_soya.c:115527: error: ‘__Pyx_InternTabEntry’ has no member named ‘p’
_soya.c: In function ‘__Pyx_InitStrings’:
_soya.c:115535: error: ‘__Pyx_StringTabEntry’ has no member named ‘p’
_soya.c:115536: error: ‘__Pyx_StringTabEntry’ has no member named ‘p’
_soya.c:115536: error: ‘__Pyx_StringTabEntry’ has no member named ‘s’
_soya.c:115536: error: ‘__Pyx_StringTabEntry’ has no member named ‘n’
_soya.c:115537: error: ‘__Pyx_StringTabEntry’ has no member named ‘p’
_soya.c: At top level:
_soya.c:115544: error: expected ‘)’ before ‘*’ token
_soya.c:115563:21: error: compile.h: No such file or directory
_soya.c:115564:25: error: frameobject.h: No such file or directory
_soya.c:115565:23: error: traceback.h: No such file or directory
_soya.c: In function ‘__Pyx_AddTraceback’:
_soya.c:115568: error: ‘PyObject’ undeclared (first use in this function)
_soya.c:115568: error: ‘py_srcfile’ undeclared (first use in this function)
_soya.c:115568: error: invalid operands to binary *
_soya.c:115569: error: ‘py_funcname’ undeclared (first use in this function)
_soya.c:115569: error: invalid operands to binary *
_soya.c:115570: error: ‘py_globals’ undeclared (first use in this function)
_soya.c:115570: error: invalid operands to binary *
_soya.c:115571: error: ‘empty_tuple’ undeclared (first use in this function)
_soya.c:115571: error: invalid operands to binary *
_soya.c:115572: error: ‘empty_string’ undeclared (first use in this function)
_soya.c:115572: error: invalid operands to binary *
_soya.c:115573: error: ‘PyCodeObject’ undeclared (first use in this function)
_soya.c:115573: error: ‘py_code’ undeclared (first use in this function)
_soya.c:115573: error: invalid operands to binary *
_soya.c:115574: error: ‘PyFrameObject’ undeclared (first use in this function)
_soya.c:115574: error: ‘py_frame’ undeclared (first use in this function)
_soya.c:115574: error: invalid operands to binary *
_soya.c:115580: error: ‘__pyx_m’ undeclared (first use in this function)
_soya.c:115610: error: request for member ‘f_lineno’ in something not a structure or union
error: command 'gcc' failed with exit status 1

What could be the problem?

---

### Post by akane on 2007-06-27
First, have you verified you have all of the dependencies for Soya3D?  

From their website:

It requires :

    * Python 2.2 or + (tested with Python 2.4)
    * OpenGL
    * OpenAL
    * GLEW
    * SDL
    * Cal3D
    * libFreeType2
    * FreeFont
    * PIL (Python Image Library) (needed for creating textures)
    * Pyrex is not needed to compile Soya, except for CVS version

---

### Post by yuvlevental on 2007-06-27
i think i do have all the requirements

---

### Post by akane on 2007-06-27
You think?  :)

What version of gcc ?
```
gcc --version
```

---

### Post by yuvlevental on 2007-06-27
but the thing is, i'm only trying to compile it because the game slune from the ubuntu repos doesn't run in python 2.5, only 2.4, so if you could tell me how to run it thru 2.4, your help would be appreciated.

---

### Post by yuvlevental on 2007-06-27
version 4.1.2, btw

---

### Post by skymera on 2007-07-22
i have 4.1.2 but i get an error too

---

