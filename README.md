
   okPushy v1.2.2
   by Oliver Kirchhoff (kirchhoff.oliver@gmail.com)
   IMDB: http://www.imdb.com/name/nm0456285/ 
   v1.0   (30/06/2014):  initial release
   v1.1   (04/12/2014):  fixed the little scale bump that
                         happened with small changes near
                         the initial position while using
                         scale compensation 
   v1.2   (04/12/2014):  Fixed serious issues with pushing
                         nurbs cv's 
   v1.2.1 (04/12/2014):  Argh! Curve cv's and surface cv's
                         are handled differently...
   v1.2.2 (08/07/2016):  Fixed the issue of okPushy to fail
                         if trying to use it on freshly created
                         primitive objects

What it does:
       This script changes the tool context. In this mode all
       selected objects or components will be pushed in camera
       space of the viewport in which the mouse is being clicked
       and dragged left/right. The pivot of the objects is
       used to calculate the "sliding rays". Therefor it works
       best if the pivots are somehow in the center of the
       objects. The tool can also be used on vertices, edges,
       polygons and nurbs cv's like curves and surfaces.
       Holding [Ctrl] while in this context makes the objects
       scale at the same time while being pushed in camera space.
       The perspective scale is being compensated this way.
       This mode is turned on by default if the last tool 
       context was scale tool rather than the move tool before
       calling the okPushy context.

usage: either call 'okPushyActivate()' as a permanent context
       or call it temporarily on a press-and-hold-hotkey
       and call 'okPushyDeactivate()' on the release-hotkey.
       Holding [Ctrl] scales objects at the same time to keep
       their size the same seen from the used viewport. This scale
       mode is also active by default it the scale context was
       the last used context before Pushy context.

bugs:  this script fails with mixed type selections, like
       vertices and objects at the same time.
       The "whatIs" return value for the source command in the
       hotkey-press event changed in some Maya versions. Please
       check what your Maya-version is returning and change the
       the comparison value for the hotkey-press event.
        
//////////////////////////////////////////////////////////////
////// Copy this to your hotkey-press event:

if (startsWith(`whatIs okPushyActivate`, "Mel") == 0) {
     source "/the/path/to/the/script/please/replace/okPushy.mel";
}
okPushyActivate();
//////////////////////////////////////////////////////////////

//////////////////////////////////////////////////////////////
////// Copy this to your hotkey-release event:

okPushyDeactivate();
//////////////////////////////////////////////////////////////
