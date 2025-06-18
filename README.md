# SideScroller-Lab
import pygame, sys
from pygame.locals import *
from Person import *

# Create a screen that is 800 by 600 pixels
pygame.init()
screen = pygame.display.set_mode((400,400))

# Every 100 milliseconds check if a key is still pressed down
# Allows user to hold down the key to move
pygame.key.set_repeat(100, 100)

# create a person named guy at position (400,400)
guy = Person(200,200)

# A list that keeps track of the areas of screen that have changed
changedRecs=[]

#draw the starting screen
WHITE = (255,255,255)
screen.fill(WHITE)
pygame.display.update()

while True:

    # draw the scene
    screen.fill(WHITE)
    
    guy.draw(screen)
    
    # adds the current position of guy to the areas that have been changed
    changedRecs.append(guy.getRec())    
    
    #update only the changed areas of the screen
    pygame.display.update(changedRecs)

    # check for events
    for event in pygame.event.get():
        if event.type==QUIT or (event.type==KEYDOWN and event.key==K_ESCAPE):
            pygame.quit()
            sys.exit()
            
        elif event.type==KEYDOWN:
            #adds the old position of guy to the areas of guy that have been changed
            changedRecs.append(guy.getRec())
            
            
            #1 fill in code for the key presses
            #1 check for which key was pressed and
            #11 use the person object's methods to
            # move guy in the correct direction
            if event.key==K_UP: 
                guy.moveUp()

            elif event.key==K_DOWN:
                guy.moveDown()

            elif event.key==K_LEFT:
                guy.moveLeft()

            elif event.key==K_RIGHT:
                guy.moveRight()
