@import 'https://unpkg.com/open-props' layer(design.system);
/_ Source code of these utilities: https://github.com/mobalti/layout-craft/blob/main/lib/utilities.css _/
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@200..700&display=swap');
@import 'https://www.unpkg.com/layout-craft@1.0.1/dist/utilities.css'
layer(base.utilities);

@layer base.app {
\*,
::before,
::after {
box-sizing: border-box;
}

:where(:not(dialog)) {
margin: 0;
padding: 0;
}
:root {
font-family: 'Inter', sans-serif;
color-scheme: dark;
--surface-1: oklch(0.17 0 0);
--surface-2: oklch(0.24 0 0);
--text-1: oklch(0.97 0 0);
--text-2: oklch(0.57 0 0);
}
body {
min-block-size: 100dvb;
background-color: var(--surface-1);
color: var(--text-1);
-webkit-font-smoothing: antialiased;
}
}

@layer components.Recommendation {
.SectionRecommendation {
/_ Adjust the inline size from here _/
--\_content: 1570px;

    /* 15px */
    font-size: 0.9375rem;

    border-block: var(--border-size-1) solid oklch(0.97 0 0 / 0.15);
    padding-block: var(--size-3);
    position: relative;
    margin-inline: auto;
    isolation: isolate;

    :where(a, button, p, span, h2) {
      font-size: inherit;
      color: inherit;
    }

    :where(button) {
      border: unset;
      cursor: pointer;
      font-family: inherit;
    }

    h2 {
      font-weight: var(--font-weight-5);
    }
    .UserList {
      list-style: none;
      overflow-x: auto;
      overscroll-behavior-x: contain;
      scroll-snap-type: x mandatory;
      scroll-behavior: smooth; /* Hide scrollbar */
      -ms-overflow-style: none; /* IE and Edge */
      scrollbar-width: none; /* Firefox */
      &::-webkit-scrollbar {
        display: none;
      }
    }
    .Card {
        background-repeat: no-repeat;
       background-size: cover;
        /*background-image: url(Cat.jpg);*/
        background-color: rgb(255, 249, 249);

      scroll-snap-align: start;
      background-color: var(--surface-2);
      border-radius: 10px;
      padding: var(--size-4);
      position: relative;
      inline-size: 356px;
      block-size: 304px;
      padding: 0.875rem;
      text-decoration: none;
      figcaption {
        --_gap: 0.2ex;
      }
      img {
        --size: 120px;
        block-size: var(--size);
        inline-size: var(--size);
        border-radius: var(--radius-round);
        background: var(--gradient-8);
      }
      .Name {
        color: var(--text-1);
        font-weight: var(--font-weight-6);
        font-size: 20px;
      }

      .Username {
        color: var(--text-2);
      }
      :is(.Name, .Username) {
        max-inline-size: 100%;
        overflow: hidden;
        white-space: nowrap;
        text-overflow: ellipsis;
        &:hover {
          text-decoration: underline;
        }
      }
      .RemoveBtn {
        background: transparent;
        border: unset;
        border-radius: var(--radius-round);
        position: absolute;
        inset-inline-end: var(--size-2);
        inset-block-start: 0.75rem;
        scale: 0.8;
        cursor: pointer;
      }
      .FollowButton {
        background-color: var(--text-1);
        color: var(--surface-1);
        font-weight: var(--font-weight-5);
        padding-inline: var(--size-5);
        border-radius: 10px;
        padding-block: var(--size-2);
        inline-size: 100%;
      }
    }
    .Controls {
      position: absolute;
      inset-inline: calc(var(--size-9) * -1);
      block-size: 204px;
      z-index: -1;
      .Wrapper {
        --_content: 700px;
      }
      @media (width < 768px) {
        display: none;
      }
    }
    .ControlsBtn {
      inline-size: 44px;
      block-size: 44px;
      padding: 0.75rem;
      border-radius: var(--radius-round);
      background-color:	#38006b;
      color: white;
      transition: 0.2s ease;
      /* Uncomment 'opacity: 0;' if you want the buttons to be visible only when you hover over the section */

/_ opacity: 0; _/

      &:hover {
        scale: 1.07;
      }
      &:active {
        scale: 1.03;
      }


    }

    &:hover {
      .ControlsBtn {
        opacity: 1;
      }
    }

    @media (width < 700px) {
      padding-inline-start: 0.75rem;
    }

}
@layer scrollDrivenAnimation {
.SectionRecommendation {
body & {
timeline-scope: --carousel;
}
.Scroller {
scroll-timeline: --carousel inline;
}
.next {
animation: auto next ease forwards;
animation-timeline: --carousel;
}
.previous {
animation: auto prev ease forwards;
animation-timeline: --carousel;
}
}

    @keyframes prev {
      from {
        visibility: hidden;
      }
    }
    @keyframes next {
      to {
        visibility: hidden;
      }
    }

}
}

.header {
position: absolute;
top: 45%;
left: 50%;
transform: translate(-50%, -50%);
font-size: 100px;

}

.nav-placeholder {
height: 4vh;
border: 1px solid red;
}
body
{
margin: 0;
padding: 0;

/_ make it look decent enough _/
background: #f4f1f4;
color: #cdcdcd;
font-family: "Avenir Next", "Avenir", sans-serif;

overflow-x: hidden; /_ needed because hiding the menu on the right side is not perfect, _/
}

a
{
text-decoration: none;
color: #232323;

transition: color 0.3s ease;
}

a:hover
{
color: tomato;
}

#menuToggle
{
display: block;
position: absolute;
top: 50px;
right: 50px;

z-index: 1;

-webkit-user-select: none;
user-select: none;
}

#menuToggle input
{
display: block;
width: 40px;
height: 32px;
position: absolute;
top: -7px;
left: -5px;

cursor: pointer;

opacity: 0; /_ hide this _/
z-index: 2; /_ and place it over the hamburger _/

-webkit-touch-callout: none;
}

/\*

- Just a quick hamburger
  \*/
  #menuToggle span
  {
  display: block;
  width: 33px;
  height: 4px;
  margin-bottom: 5px;
  position: relative;

background: #cdcdcd;
border-radius: 3px;

z-index: 1;

transform-origin: 4px 0px;

transition: transform 0.5s cubic-bezier(0.77,0.2,0.05,1.0),
background 0.5s cubic-bezier(0.77,0.2,0.05,1.0),
opacity 0.55s ease;
}

#menuToggle span:first-child
{
transform-origin: 0% 0%;
}

#menuToggle span:nth-last-child(2)
{
transform-origin: 0% 100%;
}

/\*

- Transform all the slices of hamburger
- into a crossmark.
  \*/
  #menuToggle input:checked ~ span
  {
  opacity: 1;
  transform: rotate(45deg) translate(-2px, -1px);
  background: #232323;
  }

/\*

- But let's hide the middle one.
  \*/
  #menuToggle input:checked ~ span:nth-last-child(3)
  {
  opacity: 0;
  transform: rotate(0deg) scale(0.2, 0.2);
  }

/\*

- Ohyeah and the last one should go the other direction
  \*/
  #menuToggle input:checked ~ span:nth-last-child(2)
  {
  opacity: 1;
  transform: rotate(-45deg) translate(0, -1px);
  }

/\*

- Make this absolute positioned
- at the top left of the screen
  \*/
  #menu
  {
  position: absolute;
  width: 500px;
  min-height: 320vh;
  margin: -100px 0 0 0;
  padding: 50px;
  padding-top: 125px;
  right: -100px;

background: #ededed;
list-style-type: none;
-webkit-font-smoothing: antialiased;
/_ to stop flickering of text in safari _/

transform-origin: 0% 0%;
transform: translate(100%, 0);

transition: transform 0.5s cubic-bezier(0.77,0.2,0.05,1.0);
}

#menu li
{
padding: 10px 0;
font-size: 22px;
}

/\*

- And let's fade it in from the left
  \*/
  #menuToggle input:checked ~ ul
  {
  transform: none;
  opacity: 1;
  }

@media screen and (max-width: 768px) {
#menu {
transform: none;
opacity: 0;

    transition: opacity 0.5s cubic-bezier(0.77,0.2,0.05,1.0);

}
}
.wrapper {
width: 100%;
max-width: 31.25rem;
margin: 1rem auto;

}

.label {
font-size: .625rem;
font-weight: 400;
text-transform: uppercase;
letter-spacing: +1.3px;
margin-bottom: 1rem;
}

.searchBar {
width: 100%;
display: flex;
flex-direction: row;
align-items: center;
}

#searchQueryInput {
width: 100%;
height: 2.8rem;
background: black;
outline: none;
border: none;
border-radius: 1.625rem;
padding: 0 3.5rem 0 1.5rem;
font-size: 1rem;
}

#searchQuerySubmit {
width: 3.5rem;
height: 2.8rem;
margin-left: -3.5rem;
background: none;
border: none;
outline: none;
}

#searchQuerySubmit:hover {
cursor: pointer;
}
