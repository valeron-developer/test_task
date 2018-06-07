How to create mockup from https://www.coinmarketplus.com/ page

1. First you need to go to the site by the link. After that, you need to press the right mouse button and select "save as ...". Then select the HTML file format and save the site page to your computer. It is desirable to save directly to a separate directory
2. For convenient work, we create a folder style in our directory, where we will contain all the styles of the page, the js folder for the file with scripts, the img folder, in which we will store images and the fonts folder, to save the fonts. For convenient work to change or add anything to the page, we will need to install the development environment. Personally, I use the package from the company JetBrains - PHPStorm, but you can edit using ordinary text editors, such as WordPad. In order to replace the text of the header and the font in @ font-face with a font from the OpenSans family, you need to open the downloaded HTML file through a text editor or through a program for developers. Then find the line "Live Token Sales & Upcoming ICOs ...", and change the text in quotes to any other.


Go to the link and download the desired font, for example "OpenSansRegular"
http://fonts4web.ru/opensans.html. The downloaded font is placed in the folder "fonts" 

Next, in the same file, write the path to the file with the styles: <stylesheet> type = "text / css" href = "styles / styles.css">, then create the styles.css file in the styles folder. Open this file and paste the following code:

.Live-Token{
    font-family: "OpenSansRegular";
}

@font-face {
    font-family: "OpenSansRegular";
    src: url("../fonts/OpenSansRegular/OpenSansRegular.eot");
    src: url("../fonts/OpenSansRegular/OpenSansRegular.eot?#iefix")format("embedded-opentype"),
    url("../fonts/OpenSansRegular/OpenSansRegular.woff") format("woff"),
    url("../fonts/OpenSansRegular/OpenSansRegular.ttf") format("truetype");
    font-style: normal;
    font-weight: normal;
}

So our title will change the font.

3. In the HTML file at the very bottom, before the </ body> tag, specify the path to the files with the scripts:

<script type = "text / javascript" src = "js / js.js"> </ script>
In the created js folder, create the js.js file, open it and copy the following:
$ (document) .ready (function () {
    $ (". slider"). each (function () {
        var obj = $ (this);
        $ (obj) .append ("<div class = 'nav'> </ div>");
        $ (obj) .find ("li"). each (function () {
            $ (obj) .find (". nav"). append ("<span rel = '" + $ (this) .index () + "'> </ span>"); 
            $ (this) .addClass ("slider" + $ (this) .index ());
        });
        $ (obj) .find ("span"). first (). addClass ("on"); 
    });
});
function sliderJS (obj, sl) {
    var ul = $ (sl) .find ("ul"); 
    var bl = $ (sl) .find ("li.slider" + obj); 
    var step = $ (bl) .width (); 
    $ (ul) .animate ({marginLeft: "-" + step * obj}, 500); 
}
$ (document) .on ("click", ".slider .nav span", function () {
    var sl = $ (this) .closest (". slider"); 

$(sl).find("span").removeClass("on"); 
    $(this).addClass("on"); 
    var obj = $(this).attr("rel"); 
    sliderJS(obj, sl);
    return false;
});


Open the styles.css file and add the code:

.slider {
    z-index: 9;
    width: 700px;
    height: 290px;
    overflow: hidden;
    margin: 0 0 7px;
    position: relative;
}
.slider ul,
.slider li {
    padding: 0;
    margin: 0;
    list-style-type: none;
}
.slider ul {
    width: 9999px;
}
.slider ul li {
    list-style-type: none;
    float: left;
    width: 700px;
    height: 290px;
}
.slider .nav {
    position: absolute;
    left: 295px;
    bottom: 12px;
}
.slider .nav span {
    opacity: 0.9;
    background: #fff;
    margin: 0 8px 0 0;
    width: 16px;
    height: 16px;
    border-radius: 8px;
    cursor: pointer;
    overflow: hidden;
    display: block;
    float: left;
    box-shadow: 0 1px 2px #000;
}
.slider .nav span.on {
    background: #66840f;
}

Create an img folder and copy 4 pictures to it with a * .png image, the name of the pictures should be 1,2,3,4 respectively

4. Then go to github.com, create an account (or go with an existing one), and save it there. Detailed instructions on how to use the service github is on their website:

https://guides.github.com/activities/hello-world/


