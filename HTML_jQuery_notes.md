HTML
1 -First, start with a fixed header and some of Bootstrap’s standard .navbar HTML. 

2 -Assign the class of .scroll-link to all our main nav links, and .scroll-top to our logo.

3 -create .page-section divs and some content for each page section. Each .page-section div that you want to scroll to will have a unique id for styling and targeting (ex: different background images).

4 -add data-id attributes to all the scroll links. The data-id for each link will be the same id of the page section we want to scroll to.

Note: You can also assign the .scroll-link class and data-id attribute to any links on the page, not just nav links.

The jQuery

Bootstrap takes care of the responsive navigation toggling, so the focus is on the actual page scrolling. 

1 - create a scrollToID function first 

$(document).ready(function() {
  // navigation click actions 
  
  $('.scroll-link').on('click', function(event){
    event.preventDefault();
    var sectionID = $(this).attr("data-id");
    scrollToID('#' + sectionID, 750);
  });

2 - then call that function any time a .scroll-link or .scroll-top is clicked. 
  // scroll to top action
  
  $('.scroll-top').on('click', function(event) {
    event.preventDefault();
    $('html, body').animate({scrollTop:0}, 'slow');     
  });

  // mobile nav toggle
  $('#nav-toggle').on('click', function (event) {
    event.preventDefault();
    $('#main-nav').toggleClass("open");
  });
});

  // scroll function
function scrollToID(id, speed){
  var offSet = 50;
  var targetOffset = $(id).offset().top - offSet;
  var mainNav = $('#main-nav');
  $('html,body').animate({scrollTop:targetOffset}, speed);
  if (mainNav.hasClass("open")) {
    mainNav.css("height", "1px").removeClass("in").addClass("collapse");
    mainNav.removeClass("open");
  }
}
if (typeof console === "undefined") {
    console = {
        log: function() { }
    };
}

* The jQuery knows which page section to scroll to based on the data-id attribute assigned to the link. 

* If .scroll-top links are clicked you’ll scroll right back up to the top.

ALSO, add a script to help close the menu in mobile views, otherwise the menu would stay open and require manually closing it after scroll. 
  <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js" type="text/javascript"></script>
  <script src="js/bootstrap.min.js" type="text/javascript"></script>
  <script type="text/javascript">

3 - add a class of .open to detect when the nav is toggled, and then toggle some Bootstrap classes to tell the nav to close when a link is clicked. 



  

